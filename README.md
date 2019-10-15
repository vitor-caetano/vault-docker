```
docker-compose -f docker-compose-local.yml up
docker-compose -f docker-compose-local.yml stop
docker-compose -f docker-compose-local.yml rm
```

```
$ docker exec -it vault-docker_vault_1 vault status
Key                Value
---                -----
Seal Type          shamir
Initialized        false
Sealed             true
Total Shares       0
Threshold          0
Unseal Progress    0/0
Unseal Nonce       n/a
Version            n/a
HA Enabled         true
```

```
$ docker exec -it vault-docker_vault_1 vault operator init
Unseal Key 1: dHn6svqbKBll474g/gpBFMrSgWUqNzF+twIEiDbzlld6
Unseal Key 2: p0LSulpmehk2fNCf+nJM8haoyGxKQoqalWVpXnSp9IgR
Unseal Key 3: eVTw03l4nCKpQ9PIC21DEepR2LPMudBuLcXrbWqugbvI
Unseal Key 4: Kt0/Ln0Sf833Ut5+hRttzlcBlfeGVtwry+eUqZcwH5qA
Unseal Key 5: 4MHMUxeuFT/MmCZMhzW5ioBL5kjb6vHWZTz8qo/aYk0B

Initial Root Token: s.ihYFViagHGdxPN03sFC92sIw

Vault initialized with 5 key shares and a key threshold of 3.
```

```
# run 3 times to unseal
$ docker exec -it vault-docker_vault_1 vault operator unseal
```

```
$ docker exec -it vault-docker_vault_1 vault login s.ihYFViagHGdxPN03sFC92sIw
$ docker exec -it vault-docker_vault_1 vault write foo value=bar
```
