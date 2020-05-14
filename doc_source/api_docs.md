# API documentation

- Wallet Generation API
    - [/enrollAdmin](#/enrollAdmin)
    - [/registerUser](#/registerUser)

- MongoDB API
    - [/login](#/login)
    - [/setUsers](#/setUsers)
    - [/getUsers](#/getUsers)
    - [/decryptData](#/decryptData)

- Smart Contract API
    - [/createUser](#/createUser)
    - [/getUserTxs](#/getUserTxs)
    - [/getAllUsers](#/getAllUsers)

## /enrollAdmin
To generate Admin wallet keys:

*GET method*

Response:

```json
{
    "status": "SUCCESS",
    "message": "Successfully enrolled admin user admin and imported it into the wallet"
}
```

## /registerUser
To generate user wallet keys:

*GET method*

Response:

```json
{
    "status": "SUCCESS",
    "message": "Successfully registered and enrolled user with name user1 and imported it into the wallet"
}
```

## /login
To login user:

*POST method*

The request includes the following parameters:

| Field                 | Type                       | Description             |
|:----------------------|:---------------------------|:------------------------|
| `username`            | String                     | Username                |
| `password`            | String                     | Password                |

Response:

```json
{
    "status": "SUCCESS",
    "message": "Login Successful"
}
```

## /setUsers
To update users limit:

*POST method*

The request includes the following parameters:

| Field                 | Type                       | Description             |
|:----------------------|:---------------------------|:------------------------|
| `userAccounts`        | Array                      | Array of Objects with accountId: UUID, onBoard: false. |

Request:

```json
{
	"userAccounts": [
		{
            "accountId": "5f4597e7-0fa0-46ca-b720-14bb791853b3",
            "onBoard": false
		}
	]
}
```

Response:

```json
{
    "status": "SUCCESS",
    "message": "Users added Succesfully."
}
```

## /getUsers
To get user:

*GET method*

Response:

```json
{
    "status": "SUCCESS",
    "message": "Request Succesfully.",
    "data": [
        {
            "_id": "5eba8431c08c2838d0106965",
            "accountId": "3e678b0b-601d-4851-864e-145b22cbf3a4",
            "onBoard": true,
            "__v": 0,
            "ccKey": "AC2",
            "timestamp": "2020-05-12T11:11:52.641Z"
        },
        {
            "_id": "5eba8431c08c2838d0106966",
            "accountId": "b933ec00-133d-4176-b282-a4bb19aa46e6",
            "onBoard": false,
            "__v": 0
        }
    ]
}
```

## /decryptData
To decrypt user details:

*POST method*

The request includes the following parameters:

| Field                 | Type                       | Description             |
|:----------------------|:---------------------------|:------------------------|
| `encryptedData`       | String                     | Encrypted user details. |
| `pincode`             | Integer                    | Pincode to decrypt user details. |

Request:

```json
{
    "encryptedData": "7d574640f26b5ec960a0d086d9a58be28537d98c7fd593dc4bbf17d3c90168d3d8b8509acc9876aa13",
    "pincode": 123456
}
```

Response:

```json
{
    "status": "SUCCESS",
    "message": "Decrypt Successful.",
    "data": {
        "firstname": "Block",
        "lastname": "Matrix"
    }
}
```

## /createUser
To insert user details in Blockchain:

*POST method*

The request includes the following parameters:

| Field                 | Type                       | Description             |
|:----------------------|:---------------------------|:------------------------|
| `accountId`           | String                     | Unique Accound ID. |
| `firstname`           | String                     | First name of user. |
| `lastname`            | String                     | Last name of user. |
| `status`              | String                     | Status - Active or Inactive. |

Request:

```json
{
    "accountId": "b933ec00-133d-4176-b282-a4bb19aa46e6",
    "firstname": "Block",
    "lastname": "Matrix",
    "status": "Active"
}
```

Response:

```json
{
    "status": "SUCCESS",
    "message": "Transaction has been submitted"
}
```

## /getUserTxs
To get user Transactions from Blockchain:

*POST method*

The request includes the following parameters:

| Field                 | Type                       | Description             |
|:----------------------|:---------------------------|:------------------------|
| `accountId`           | String                     | Unique User Accound ID. |

Request:

```json
{
    "accountId": "a875fb0e-222a-4c41-a751-09098d35d3a3"
}
```

Response:

```json
{
    "status": "SUCCESS",
    "data": [
        {
            "TxId": "b2c590bae34ffaaba1f0a068b12bde687fcce96a49c91eaeb6a9a8af342016a7",
            "Value": {
                "account_id": "a875fb0e-222a-4c41-a751-09098d35d3a3",
                "status": "Active",
                "sensitive_data": "7d574640f26b5ec960a0d086d9a59aef9835c6c671dbddd159b80ddcc5092fcbc0d77a8fd2947dff0fbf3398401d"
            },
            "Timestamp": "2020-04-20 09:40:02.552 +0000 UTC",
            "IsDelete": "false"
        }
    ]
}
```

## /getAllUsers
To get users from Blockchain:

*GET method*

Response:

```json
{
    "status": "SUCCESS",
    "data": [
        {
            "Key": "AC0",
            "Record": {
                "account_id": "a875fb0e-222a-4c41-a751-09098d35d3a3",
                "sensitive_data": "7d574640f26b5ec960a0d086d9a59aef9835c6c671dbddd159b80ddcc5092fcbc0d77a8fd2947dff0fbf3398401d",
                "status": "Active"
            }
        },
        {
            "Key": "AC1",
            "Record": {
                "account_id": "8a8b33c3-c9d7-4ea6-9e74-c7820812e155",
                "sensitive_data": "7d574640f26b5ec960a0d086d9a58be28537d98c7fd593dc4bbf17d3c90168d3d8b8509acc9876aa13",
                "status": "Active"
            }
        }
    ]
}
```
