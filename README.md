[![1](https://github.com/rozoandrescamilo/Smart-Contract-para-consultar-estados-de-una-Purchase-Order/blob/main/img/1.jpg?raw=true "1")](https://github.com/Smart-Contract-para-consultar-estados-de-una-Purchase-Order/blob/main/img/1.jpg?raw=true "1")

- [Documentación de la API REST de Kaleido para integración con Frontend](#documentación-de-la-api-rest-de-kaleido-para-integración-con-frontend)
  - [Despliege de smart contract en la API](#despliege-de-smart-contract-en-la-api)
    - [Creación y despliegue de nuevo smart contract](#creación-y-despliegue-de-nuevo-smart-contract)
    - [Gestión de smart contract con REST API Gateway](#gestión-de-smart-contract-con-rest-api-gateway)
  - [Gestión y documentación de REST API con POSTMAN](#gestión-y-documentación-de-rest-api-con-postman)
  - [Interactuar con la consulta de estados de una Purchase Order](#interactuar-con-la-consulta-de-estados-de-una-purchase-order)
    - [Registrar una nueva Purchase Order](#registrar-una-nueva-purchase-order)
    - [Validar estado de la Purchase Order](#validar-estado-de-la-purchase-order)
    - [Registrar paso en la Purchase Order](#registrar-una-nueva-purchase-order)


# Documentación de la API REST de Kaleido para integración con Frontend

## Despliege de smart contract en la API

### Creación y despliegue de nuevo smart contract 

Como requisito es necesario tener una cuenta en la Página oficial de la consola de Kaleido: [https://console.kaleido.io/login](https://console.kaleido.io/login "https://console.kaleido.io/login"), también será necesario tener creados en la cuenta una Network, un entorno de trabajo, un Supernodo Firefly inicializado y una App para la gestión de contratos empresariales de Kaleido.

Dentro de la App creada se inicia un nuevo smart contract, para este caso se selecciona Github para importar el archivo del contrato:

[![1](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/1.png?raw=true "1")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/1.png?raw=true "1")

Luego, se deben ingresar los detalles del proyecto como nombre, versión, la URL del repositorio de Github donde se encuentra el contrato inteligente y la versión del compilador de la EVM - Ethereum Virtual Machine.

Para este proceso se utiliza el contrato <StatusValidator.sol>, un contrato inteligente que tiene como fin crear un método para consultar los diferentes estados posibles de una Purchase Order desde CONFIRMED PO hasta COMPLETED. Se recomienda ver el funcionamiento de este contrato para entender de mejor manera: [https://github.com/rozoandrescamilo/Smart-Contract-para-consultar-estados-de-una-Purchase-Order](https://github.com/rozoandrescamilo/Smart-Contract-para-consultar-estados-de-una-Purchase-Order "https://github.com/rozoandrescamilo/Smart-Contract-para-consultar-estados-de-una-Purchase-Order")

[![2](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/2.png?raw=true "2")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/2.png?raw=true "2")

Creada la nueva instancia del contrato se adiciona la Gateway API que es una consola Swagger para la gestión del contrato y transacciones.

[![3](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/3.png?raw=true "3")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/3.png?raw=true "3")

Una vez finalizado el ingreso de detalles se mostrará los parametros de la versión y el contrato debe pasar de status Compiling a Compiled para poder continuar.

[![4](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/4.png?raw=true "4")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/4.png?raw=true "4")

Después se mostrará detalles del Smart Contract donde se podran realizar varias actividades con API GATEWAY:

- Crear una API de puerta de enlace: crea una consola swagger dinámica y una especificación descargable para la interacción RESTful con métodos de contrato inteligente.

- Implementar contratos: use la API de Gateway para implementar su contrato inteligente mediante programación o directamente a través de la consola.

- Enviar transacciones: Aproveche la API para interactuar con contratos inteligentes en cadena existentes al pasar la dirección del contrato como parámetro en la llamada.

[![5](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/5.png?raw=true "5")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/5.png?raw=true "5")

### Gestión de smart contract con REST API Gateway

La interfaz de usuario Swagger incorporada se despliega dando clic en el boton VIEW GATEWAY API y se pueden visualizar los servicios web de acceso y gestión de datos de organizaciones y proyectos a través de REST APIs.

[![6](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/6.png?raw=true "6")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/6.png?raw=true "6")

En el POST/constructor() se debe agregar el archivo ABI de la compilación del contrato y hacer clic en EJECUTAR.

[![7](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/7.png?raw=true "7")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/7.png?raw=true "7")

ABI del contrato compilado:

```javascript
{
  "input": {
    "abi": [
      {
        "anonymous": false,
        "inputs": [
          {
            "indexed": false,
            "internalType": "uint256",
            "name": "POID",
            "type": "uint256"
          },
          {
            "indexed": false,
            "internalType": "enum StatusValidator.Status",
            "name": "status",
            "type": "uint8"
          },
          {
            "indexed": false,
            "internalType": "string",
            "name": "metadata",
            "type": "string"
          },
          {
            "indexed": false,
            "internalType": "address",
            "name": "author",
            "type": "address"
          }
        ],
        "name": "RegisteredStep",
        "type": "event"
      },
      {
        "inputs": [
          {
            "internalType": "uint256",
            "name": "",
            "type": "uint256"
          },
          {
            "internalType": "uint256",
            "name": "",
            "type": "uint256"
          }
        ],
        "name": "POvalidator",
        "outputs": [
          {
            "internalType": "enum StatusValidator.Status",
            "name": "status",
            "type": "uint8"
          },
          {
            "internalType": "string",
            "name": "metadata",
            "type": "string"
          }
        ],
        "stateMutability": "view",
        "type": "function"
      },
      {
        "inputs": [
          {
            "internalType": "uint256",
            "name": "POID",
            "type": "uint256"
          }
        ],
        "name": "registerPO",
        "outputs": [
          {
            "internalType": "bool",
            "name": "success",
            "type": "bool"
          }
        ],
        "stateMutability": "nonpayable",
        "type": "function"
      },
      {
        "inputs": [
          {
            "internalType": "uint256",
            "name": "POID",
            "type": "uint256"
          },
          {
            "internalType": "string",
            "name": "metadata",
            "type": "string"
          }
        ],
        "name": "registerStep",
        "outputs": [
          {
            "internalType": "bool",
            "name": "success",
            "type": "bool"
          }
        ],
        "stateMutability": "nonpayable",
        "type": "function"
      }
    ]
  }
}

```

Como respuesta se obtiene un archivo JSON donde se realiza una solicitud POST usando la API de Kaleido. Esta solicitud se utiliza para crear una nueva puerta de enlace en la red Kaleido. El contenido del archivo JSON incluye información sobre los parámetros de la solicitud, tales como la dirección de la cuenta de la que se va a realizar la solicitud, la ABI de la aplicación, entre otros.

[![8](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/8.png?raw=true "8")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/8.png?raw=true "8")

## Gestión y documentación de REST API con POSTMAN

Para generar la documentación necesaria para la integración con Frontend, se utiliza la aplicación de escritorio POSTMAN que es una herramienta para el desarrollo de APIs que facilita el diseño, el testing y el monitoreo de servicios REST. Sirve para probar endpoints de aplicaciones web basadas en APIs o REST. Con POSTMAN, los desarrolladores pueden configurar, enviar y guardar solicitudes HTTP y ver sus respuestas. Esto les permite hacer pruebas más rápidas y los ayuda a comprender mejor sus APIs y cómo interactúan con otros sistemas. Postman también ayuda a los desarrolladores a documentar mejor sus APIs, lo que facilita su uso para otros desarrolladores.

Se selecciona el boton SEND A REQUEST para comenzar la interacción.

[![9](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/9.png?raw=true "9")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/9.png?raw=true "9")

Teniendo en cuenta el archivo JSON de respuesta por ejecutar el ABI en la REST API de Kaleido, se debe extraer la URL del Curl: "https://u1my9uxwbm-u1bzt3mvmy-connect.us1-azure.kaleido.io/gateways/u1hudakhgw/?kld-from=0xf0afc19d9108b443096f0de4d461093b106b3bcd&kld-sync=true" y agregarla como un llamado POST. Al ingresar el link reconoce parámetros de la API en la pestaña **Params.** 

[![10](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/10.png?raw=true "10")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/10.png?raw=true "10")

Luego, en la pestaña **Headers** se debe agregar la Key "Authorization" y como valor "Basic dTFyNnIyZGxwczo5R1c4clJJbjNnaUR6akE3aVVKVVRwRHFsemVNdTM3V1ducm1PMkg4MlpJ" que se encuentra en el archivo JSON de salida por ejecutar el ABI en la REST API de Kaleido.

[![11](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/11.png?raw=true "11")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/11.png?raw=true "11")

En la pestaña de **Body** se selecciona el tipo Raw ya que es texto plano y el archivo de tipo JSON, dentro de este se debe pegar el archivo ABI de la compilación del contrato. Una vez realizada esta configuración ya es posible dar clic en **Send** para enviar la solicitud a la API.

[![12](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/12.png?raw=true "12")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/12.png?raw=true "12")

Se obtendra como output una respuesta del servidor similar a la de API REST de Kaliedo, donde se pueden ver parámetros de la transacción realizada, que le pueden ser de interés al usuario a lo largo de todo el flujo del proceso en la gestión de datos. Algunos de los términos relevantes en la respuesta incluyen:

- **contractAddress:** se refiere a la dirección del contrato inteligente utilizado en la transacción.

- **gasUsed y cumulativeGasUsed:** se refieren a la cantidad de gas utilizada en la transacción. El gas es una unidad de medida utilizada en Ethereum (la plataforma blockchain en la que se basa Kaleido) para calcular el costo de las transacciones.

- **transactionHash:** se refiere al hash único de la transacción en la cadena de bloques.

- **blockHash:** hace referencia al algoritmo que representa la dirección del bloque utilizado en la transacción.

- **blockNumber:** número del bloque utilizado en la transacción.

[![13](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/13.png?raw=true "13")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/13.png?raw=true "13")

Respuesta de POSTMAN:

```javascript
{
    "headers": {
        "id": "acf61f66-6d75-49fb-631c-feb6f4dc101d",
        "type": "TransactionSuccess",
        "ctx": {
            "isRemoteRegistry": true
        },
        "timeReceived": "2023-02-25T00:33:21.419020976Z",
        "timeElapsed": 6.217451651,
        "requestOffset": "",
        "requestId": "655217cd-04f9-41be-5935-5fb40bea9f52",
        "requestABIId": "u1hudakhgw"
    },
    "blockHash": "0xc7ef76b2423393da318f86f9df5cb0b516367fb84f7afd3d5d0d386412bae485",
    "blockNumber": "75727",
    "openapi": "https://u1my9uxwbm-u1bzt3mvmy-connect.us1-azure.kaleido.io/instances/35aac50f63e614e158f2f33aae23c6c50ec75785?openapi",
    "apiexerciser": "https://u1my9uxwbm-u1bzt3mvmy-connect.us1-azure.kaleido.io/instances/35aac50f63e614e158f2f33aae23c6c50ec75785?ui",
    "contractAddress": "0x35aac50f63e614e158f2f33aae23c6c50ec75785",
    "cumulativeGasUsed": "916454",
    "from": "0xf0afc19d9108b443096f0de4d461093b106b3bcd",
    "gasUsed": "916454",
    "nonce": "0",
    "status": "1",
    "to": null,
    "transactionHash": "0x3721f0d01f2cecdeeb2f62e01cbba13e40541742de09706102a5c8bca3417e4e",
    "transactionIndex": "0"
}

```

En la parte derecha de POSTMAN en la pestaña **</>** se puede obtener el fragmento de código resultante, que servirá como documentación necesaria para la integración con el equipo de Frontend. Este fragmento es un archivo JSON con un formato de intercambio de datos utilizado para transmitir información en formato de texto entre diferentes aplicaciones. En este caso, el archivo JSON se está utilizando para realizar una solicitud POST usando la API de Kaleido. Esta solicitud se utiliza para crear una nueva puerta de enlace en la red Kaleido. El contenido del archivo JSON incluye información sobre los parámetros de la solicitud, tales como la dirección de la cuenta de la que se va a realizar la solicitud, la ABI de la aplicación, entre otros.

[![14](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/14.png?raw=true "14")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/14.png?raw=true "14")

Código JSON para documentación:

```javascript
curl --location 'https://u1my9uxwbm-u1bzt3mvmy-connect.us1-azure.kaleido.io/gateways/u1hudakhgw/?kld-from=0xf0afc19d9108b443096f0de4d461093b106b3bcd&kld-sync=true' \
--header 'Authorization: Basic dTFyNnIyZGxwczo5R1c4clJJbjNnaUR6akE3aVVKVVRwRHFsemVNdTM3V1ducm1PMkg4MlpJ' \
--header 'Content-Type: application/json' \
--data '{
  "input": {
    "abi": [
      {
        "anonymous": false,
        "inputs": [
          {
            "indexed": false,
            "internalType": "uint256",
            "name": "POID",
            "type": "uint256"
          },
          {
            "indexed": false,
            "internalType": "enum StatusValidator.Status",
            "name": "status",
            "type": "uint8"
          },
          {
            "indexed": false,
            "internalType": "string",
            "name": "metadata",
            "type": "string"
          },
          {
            "indexed": false,
            "internalType": "address",
            "name": "author",
            "type": "address"
          }
        ],
        "name": "RegisteredStep",
        "type": "event"
      },
      {
        "inputs": [
          {
            "internalType": "uint256",
            "name": "",
            "type": "uint256"
          },
          {
            "internalType": "uint256",
            "name": "",
            "type": "uint256"
          }
        ],
        "name": "POvalidator",
        "outputs": [
          {
            "internalType": "enum StatusValidator.Status",
            "name": "status",
            "type": "uint8"
          },
          {
            "internalType": "string",
            "name": "metadata",
            "type": "string"
          }
        ],
        "stateMutability": "view",
        "type": "function"
      },
      {
        "inputs": [
          {
            "internalType": "uint256",
            "name": "POID",
            "type": "uint256"
          }
        ],
        "name": "registerPO",
        "outputs": [
          {
            "internalType": "bool",
            "name": "success",
            "type": "bool"
          }
        ],
        "stateMutability": "nonpayable",
        "type": "function"
      },
      {
        "inputs": [
          {
            "internalType": "uint256",
            "name": "POID",
            "type": "uint256"
          },
          {
            "internalType": "string",
            "name": "metadata",
            "type": "string"
          }
        ],
        "name": "registerStep",
        "outputs": [
          {
            "internalType": "bool",
            "name": "success",
            "type": "bool"
          }
        ],
        "stateMutability": "nonpayable",
        "type": "function"
      }
    ]
  }
}'

```

## Interactuar con la consulta de estados de una Purchase Order

### Registrar una nueva Purchase Order

En la API REST de Kaleido en la sección **POST/{address}/registerPO** se puede registrar una nueva Purchase Order de un Usuario con un ID: "1234". Se requiere como parámetros la dirección del smart contract y en el body el ID de la Order, después de esto se puede ejecutar.

[![15](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/15.png?raw=true "15")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/15.png?raw=true "15")

En la respuesta del servidor muestra el Curl con el link y la key de autorización, también muestra la respuesta con toda la información de la transacción realizada para registrar la nueva order.

[![16](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/16.png?raw=true "16")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/16.png?raw=true "16")

Respuesta del servidor:

```javascript
{
  "headers": {
    "id": "123d8914-838a-463e-480f-3eb05a3cdc40",
    "type": "TransactionSuccess",
    "timeReceived": "2023-02-25T03:23:58.154709313Z",
    "timeElapsed": 4.621957555,
    "requestOffset": "",
    "requestId": "e2a3a037-9ca7-40f1-58ec-5371808e9363"
  },
  "blockHash": "0xd55d301af847a41a8b217cbcb0b8dead6d9e185e83250797df9dc7c23868f209",
  "blockNumber": "77774",
  "cumulativeGasUsed": "49553",
  "from": "0xf0afc19d9108b443096f0de4d461093b106b3bcd",
  "gasUsed": "49553",
  "nonce": "0",
  "status": "1",
  "to": "0x35aac50f63e614e158f2f33aae23c6c50ec75785",
  "transactionHash": "0xa142a03aa4cf1ce8c243eae6406db016b96a294315f73ace4d43a4160e89d3bd",
  "transactionIndex": "0"
}

```

Al intentar registrar la PO on el mismo ID directamente en POSTMAN, se logra comprobar mediante un error que la Purchase Order ya existe en la instancia del contrato. 

[![17](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/17.png?raw=true "17")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/17.png?raw=true "17")

Código JSON para documentación:

```javascript
curl --location 'https://u1my9uxwbm-u1bzt3mvmy-connect.us1-azure.kaleido.io/gateways/u1hudakhgw/0x35aac50f63e614e158f2f33aae23c6c50ec75785/registerPO?kld-from=0xf0afc19d9108b443096f0de4d461093b106b3bcd&kld-sync=true' \
--header 'Authorization: Basic dTFyNnIyZGxwczo5R1c4clJJbjNnaUR6akE3aVVKVVRwRHFsemVNdTM3V1ducm1PMkg4MlpJ' \
--header 'Content-Type: application/json' \
--data '{
  "POID": "1234"
}'
```

### Validar estado de la Purchase Order

En la API REST de Kaleido en la sección **POST/{address}/POvalidator** con el ID de la Purchase Order y el número "0" que equivale al estado "CONFIRMED_PO", se puede hacer un llamado al smart contract y muestra como salida el status actual de la PO y un string que puede contener metadata del proceso hasta el momento. 

Se debe tener en cuenta los diferentes status y su posición:

- CONFIRMED_PO = status 0
- BOOKING_REQUEST = status 1
- SHIPMENT_IN_TRANSIT = status 2
- SHIPMENT_AT_DESTINATION = status 3
- CUSTOMS = status 4
- DELIVERED = status 5
- COMPLETED = status 6

[![18](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/18.png?raw=true "18")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/18.png?raw=true "18")

[![19](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/19.png?raw=true "19")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/19.png?raw=true "19")

Se obtiene una respuesta correcta indicando que la Purchase Order esta en el estado CONFIRMED_PO = status 0. Se realiza la respectiva configuración en POSTMAN del método y se obtiene el mismo resultado.

[![20](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/20.png?raw=true "20")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/20.png?raw=true "20")

Respuesta de POSTMAN:

```javascript
{
    "metadata": "",
    "status": "0"
}

```

Código JSON para documentación:

```javascript
curl --location 'https://u1my9uxwbm-u1bzt3mvmy-connect.us1-azure.kaleido.io/gateways/u1hudakhgw/0x35aac50f63e614e158f2f33aae23c6c50ec75785/POvalidator?kld-from=0xf0afc19d9108b443096f0de4d461093b106b3bcd&kld-sync=true' \
--header 'Authorization: Basic dTFyNnIyZGxwczo5R1c4clJJbjNnaUR6akE3aVVKVVRwRHFsemVNdTM3V1ducm1PMkg4MlpJ' \
--header 'Content-Type: application/json' \
--data '{
  "input": "1234",
  "input1": "0"
}'

```

### Registrar paso en la Purchase Order

En la API REST de Kaleido en la sección **POST/{address}/registerStep** con los datos del ID de la Purchase Order y como ejemplo de metadata "BOOKING_REQUEST OK" se registra un nuevo step en el contrato y se hace la ejecución de la transacción.

[![21](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/21.png?raw=true "21")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/21.png?raw=true "21")

De manera efectiva se obtiene la información de la transacción en la red blockchain donde ahora el status de la order "1234" es BOOKING_REQUEST = status 1.

[![22](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/22.png?raw=true "22")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/22.png?raw=true "22")

Respuesta del servidor:

```javascript
{
  "headers": {
    "id": "689c195d-b21c-4906-612e-57e6b6c80f9a",
    "type": "TransactionSuccess",
    "timeReceived": "2023-02-25T04:00:02.325529952Z",
    "timeElapsed": 5.402202702,
    "requestOffset": "",
    "requestId": "4e73e053-afa1-46a6-4edf-caee6b8b5eb6"
  },
  "blockHash": "0xd722072dce0288304380e749b637e6e1184f3f1447756e6cfe67c355b9b22c7d",
  "blockNumber": "78207",
  "cumulativeGasUsed": "82325",
  "from": "0xf0afc19d9108b443096f0de4d461093b106b3bcd",
  "gasUsed": "82325",
  "nonce": "0",
  "status": "1",
  "to": "0x35aac50f63e614e158f2f33aae23c6c50ec75785",
  "transactionHash": "0xe2fa2b0b72b6591f4d61bdcb09227f0eb9ef1393df92144cf9de6afb9bce45ef",
  "transactionIndex": "0"
}
```
Usando el POSTMAN de POvalidator se puede verificar que la PO "1234" si se encuentra en status 1.

[![23](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/23.png?raw=true "23")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/23.png?raw=true "23")

Código JSON para documentación:

```javascript
curl --location 'https://u1my9uxwbm-u1bzt3mvmy-connect.us1-azure.kaleido.io/gateways/u1hudakhgw/0x35aac50f63e614e158f2f33aae23c6c50ec75785/POvalidator?kld-from=0xf0afc19d9108b443096f0de4d461093b106b3bcd&kld-sync=true' \
--header 'Authorization: Basic dTFyNnIyZGxwczo5R1c4clJJbjNnaUR6akE3aVVKVVRwRHFsemVNdTM3V1ducm1PMkg4MlpJ' \
--header 'Content-Type: application/json' \
--data '{
  "input": "1234",
  "input1": "1"
}'

```

El código permite registrar y validar los siguientes estados hasta que la PO se encuentre COMPLETED.

- SHIPMENT_IN_TRANSIT = status 2

[![24](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/24.png?raw=true "24")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/24.png?raw=true "24")

Respuesta de POSTMAN:

```javascript
{
    "headers": {
        "id": "a18075c9-142f-4196-6fd1-50d7548ed481",
        "type": "TransactionSuccess",
        "timeReceived": "2023-02-25T04:09:54.519863557Z",
        "timeElapsed": 4.501385691,
        "requestOffset": "",
        "requestId": "401d2660-6693-4672-7513-dd7fbff31543"
    },
    "blockHash": "0xed7c80a647fb11cc2d2f31f56c530cefba188558df74804c2ddfde98c45ab3ec",
    "blockNumber": "78325",
    "cumulativeGasUsed": "87517",
    "from": "0xf0afc19d9108b443096f0de4d461093b106b3bcd",
    "gasUsed": "87517",
    "nonce": "0",
    "status": "1",
    "to": "0x35aac50f63e614e158f2f33aae23c6c50ec75785",
    "transactionHash": "0xdb42a202ffb110b91b0841ca2c4785c4ba7279648945be5999ced1029f06e8dc",
    "transactionIndex": "0"
}

```

Código JSON para documentación:

```javascript
curl --location 'https://u1my9uxwbm-u1bzt3mvmy-connect.us1-azure.kaleido.io/gateways/u1hudakhgw/0x35aac50f63e614e158f2f33aae23c6c50ec75785/registerStep?kld-from=0xf0afc19d9108b443096f0de4d461093b106b3bcd&kld-sync=true' \
--header 'Authorization: Basic dTFyNnIyZGxwczo5R1c4clJJbjNnaUR6akE3aVVKVVRwRHFsemVNdTM3V1ducm1PMkg4MlpJ' \
--header 'Content-Type: application/json' \
--data '{
  "POID": "1234",
  "metadata": "SHIPMENT_IN_TRANSIT OK"
}'

```

- SHIPMENT_AT_DESTINATION = status 3

[![25](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/25.png?raw=true "25")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/25.png?raw=true "25")

Respuesta de POSTMAN:

```javascript
{
    "headers": {
        "id": "e4c6f07f-0467-4262-6d40-e91ab6478ec2",
        "type": "TransactionSuccess",
        "timeReceived": "2023-02-25T05:19:33.542168696Z",
        "timeElapsed": 4.420160924,
        "requestOffset": "",
        "requestId": "b8c2e345-1b5a-4f85-582a-6f293c146993"
    },
    "blockHash": "0x3f24d959f83f8fd867b92c5e1bd520a3896032cf02afc18c8f336a42268ad2a5",
    "blockNumber": "79161",
    "cumulativeGasUsed": "92708",
    "from": "0xf0afc19d9108b443096f0de4d461093b106b3bcd",
    "gasUsed": "92708",
    "nonce": "0",
    "status": "1",
    "to": "0x35aac50f63e614e158f2f33aae23c6c50ec75785",
    "transactionHash": "0xf679055df2a4eb7bdd1e74ba241edf7da9045cd5a4d90d2646cbfce80a903101",
    "transactionIndex": "0"
}

```

Código JSON para documentación:

```javascript
curl --location 'https://u1my9uxwbm-u1bzt3mvmy-connect.us1-azure.kaleido.io/gateways/u1hudakhgw/0x35aac50f63e614e158f2f33aae23c6c50ec75785/registerStep?kld-from=0xf0afc19d9108b443096f0de4d461093b106b3bcd&kld-sync=true' \
--header 'Authorization: Basic dTFyNnIyZGxwczo5R1c4clJJbjNnaUR6akE3aVVKVVRwRHFsemVNdTM3V1ducm1PMkg4MlpJ' \
--header 'Content-Type: application/json' \
--data '{
  "POID": "1234",
  "metadata": "SHIPMENT_AT_DESTINATION OK"
}'

```

- CUSTOMS = status 4

[![26](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/26.png?raw=true "26")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/26.png?raw=true "26")

Respuesta de POSTMAN:

```javascript
{
    "headers": {
        "id": "ad0e6ef1-3096-41ae-5829-4e9a553a14ba",
        "type": "TransactionSuccess",
        "timeReceived": "2023-02-25T05:21:50.725911627Z",
        "timeElapsed": 6.29405446,
        "requestOffset": "",
        "requestId": "ab7e9fb9-91e0-40d1-413d-2c61d1e17b4b"
    },
    "blockHash": "0xd628c029f1d0840f8c7c31c83ed3e821781077d81aaa0c9640cc0b8cafdba8e7",
    "blockNumber": "79189",
    "cumulativeGasUsed": "97660",
    "from": "0xf0afc19d9108b443096f0de4d461093b106b3bcd",
    "gasUsed": "97660",
    "nonce": "0",
    "status": "1",
    "to": "0x35aac50f63e614e158f2f33aae23c6c50ec75785",
    "transactionHash": "0x54c255b8874afc71d7127800493d5d534c82e2b29d6f72d27b079423b38ef16f",
    "transactionIndex": "0"
}

```

Código JSON para documentación:

```javascript
curl --location 'https://u1my9uxwbm-u1bzt3mvmy-connect.us1-azure.kaleido.io/gateways/u1hudakhgw/0x35aac50f63e614e158f2f33aae23c6c50ec75785/registerStep?kld-from=0xf0afc19d9108b443096f0de4d461093b106b3bcd&kld-sync=true' \
--header 'Authorization: Basic dTFyNnIyZGxwczo5R1c4clJJbjNnaUR6akE3aVVKVVRwRHFsemVNdTM3V1ducm1PMkg4MlpJ' \
--header 'Content-Type: application/json' \
--data '{
  "POID": "1234",
  "metadata": "CUSTOMS OK"
}'

```

- DELIVERED = status 5

[![27](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/27.png?raw=true "27")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/27.png?raw=true "27")

Respuesta de POSTMAN:

```javascript
{
    "headers": {
        "id": "657b1193-655b-4562-5236-8c0fb0302744",
        "type": "TransactionSuccess",
        "timeReceived": "2023-02-25T05:24:27.082544577Z",
        "timeElapsed": 6.370812683,
        "requestOffset": "",
        "requestId": "69615e10-4f7e-4fb7-60eb-fa702972d9ec"
    },
    "blockHash": "0xc77f7340764b721d125d608939b00f68dde391beb67016ed0e798dcd49d79ed6",
    "blockNumber": "79220",
    "cumulativeGasUsed": "102828",
    "from": "0xf0afc19d9108b443096f0de4d461093b106b3bcd",
    "gasUsed": "102828",
    "nonce": "0",
    "status": "1",
    "to": "0x35aac50f63e614e158f2f33aae23c6c50ec75785",
    "transactionHash": "0x81d6bed2f7d6e81c526d34cf65aebca04e6986c6326212b1be30d4ee493bbe4e",
    "transactionIndex": "0"
}

```

Código JSON para documentación:

```javascript
curl --location 'https://u1my9uxwbm-u1bzt3mvmy-connect.us1-azure.kaleido.io/gateways/u1hudakhgw/0x35aac50f63e614e158f2f33aae23c6c50ec75785/registerStep?kld-from=0xf0afc19d9108b443096f0de4d461093b106b3bcd&kld-sync=true' \
--header 'Authorization: Basic dTFyNnIyZGxwczo5R1c4clJJbjNnaUR6akE3aVVKVVRwRHFsemVNdTM3V1ducm1PMkg4MlpJ' \
--header 'Content-Type: application/json' \
--data '{
  "POID": "1234",
  "metadata": "DELIVERED OK"
}'

```

- COMPLETED = status 6

[![27](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/27.png?raw=true "27")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/27.png?raw=true "27")

Respuesta de POSTMAN:

```javascript
{
    "headers": {
        "id": "e4168134-1fc3-4672-757d-fe3cdaebf344",
        "type": "TransactionSuccess",
        "timeReceived": "2023-02-25T05:27:03.324533848Z",
        "timeElapsed": 4.451673867,
        "requestOffset": "",
        "requestId": "ca1e36a9-e1fa-4197-77dc-46386a063208"
    },
    "blockHash": "0x81d3fa7ab0eb7663701448b066efcb42932fe54ee35d754863aff42ba1d40e1b",
    "blockNumber": "79251",
    "cumulativeGasUsed": "107971",
    "from": "0xf0afc19d9108b443096f0de4d461093b106b3bcd",
    "gasUsed": "107971",
    "nonce": "0",
    "status": "1",
    "to": "0x35aac50f63e614e158f2f33aae23c6c50ec75785",
    "transactionHash": "0xf68aefa0f22bc6a4e5430f8e53a8438de643231eb74ba22e362f4527d8d24db5",
    "transactionIndex": "0"
}

```

Código JSON para documentación:

```javascript
curl --location 'https://u1my9uxwbm-u1bzt3mvmy-connect.us1-azure.kaleido.io/gateways/u1hudakhgw/0x35aac50f63e614e158f2f33aae23c6c50ec75785/registerStep?kld-from=0xf0afc19d9108b443096f0de4d461093b106b3bcd&kld-sync=true' \
--header 'Authorization: Basic dTFyNnIyZGxwczo5R1c4clJJbjNnaUR6akE3aVVKVVRwRHFsemVNdTM3V1ducm1PMkg4MlpJ' \
--header 'Content-Type: application/json' \
--data '{
  "POID": "1234",
  "metadata": "COMPLETED OK"
}'

```

Al intentar registrar otro paso para la PO que ya paso a estado COMPLETED, se genera el error: "The Purchase Order has no more steps", evitando que se incurra en pasos extra.

[![29](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/29.png?raw=true "29")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/29.png?raw=true "29")

Respuesta de POSTMAN:

```javascript
{
    "error": "Call failed: execution reverted: The Purchase Order has no more steps",
    "code": "FFEC100148"
}

```
Otra función que permite el smart contract es validar estados anteriores junto con la metadata que quedo atada a este step, para esto se utiliza el POSTMAN de POvalidator que puede verificar quelos status de la PO "1234".

[![30](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/30.png?raw=true "30")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/30.png?raw=true "30")

Respuesta de POSTMAN:

```javascript
{
    "metadata": "DELIVERED OK",
    "status": "5"
}

```

Código JSON para documentación:

```javascript
curl --location 'https://u1my9uxwbm-u1bzt3mvmy-connect.us1-azure.kaleido.io/gateways/u1hudakhgw/0x35aac50f63e614e158f2f33aae23c6c50ec75785/POvalidator?kld-from=0xf0afc19d9108b443096f0de4d461093b106b3bcd&kld-sync=true' \
--header 'Authorization: Basic dTFyNnIyZGxwczo5R1c4clJJbjNnaUR6akE3aVVKVVRwRHFsemVNdTM3V1ducm1PMkg4MlpJ' \
--header 'Content-Type: application/json' \
--data '{
  "input": "1234",
  "input1": "5"
}'

```

[![31](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/31.png?raw=true "31")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/31.png?raw=true "31")

Respuesta de POSTMAN:

```javascript
{
    "metadata": "COMPLETED OK",
    "status": "6"
}

```

Código JSON para documentación:

```javascript
curl --location 'https://u1my9uxwbm-u1bzt3mvmy-connect.us1-azure.kaleido.io/gateways/u1hudakhgw/0x35aac50f63e614e158f2f33aae23c6c50ec75785/POvalidator?kld-from=0xf0afc19d9108b443096f0de4d461093b106b3bcd&kld-sync=true' \
--header 'Authorization: Basic dTFyNnIyZGxwczo5R1c4clJJbjNnaUR6akE3aVVKVVRwRHFsemVNdTM3V1ducm1PMkg4MlpJ' \
--header 'Content-Type: application/json' \
--data '{
  "input": "1234",
  "input1": "6"
}'

```

También facilita que al momento de crear otros Purchase Orders con otros ID y otros status diferentes, se pueda validar datos de un PO anterior o diferente al que se está trabajando en la misma instancia.

Crear una nueva PO:

[![32](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/32.png?raw=true "32")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/32.png?raw=true "32")

Respuesta de POSTMAN:

```javascript
{
    "headers": {
        "id": "0db6399c-b909-4410-786e-3b2af3fa243b",
        "type": "TransactionSuccess",
        "timeReceived": "2023-02-25T05:41:36.967209803Z",
        "timeElapsed": 6.357196925,
        "requestOffset": "",
        "requestId": "9f939ce6-7a85-4b39-44d6-2e2c1da1ead0"
    },
    "blockHash": "0x1b61db3ec9b9d0d47120e272141b3c7d8dd6f9d7581b9cc8f48dba9f458065ae",
    "blockNumber": "79426",
    "cumulativeGasUsed": "49553",
    "from": "0xf0afc19d9108b443096f0de4d461093b106b3bcd",
    "gasUsed": "49553",
    "nonce": "0",
    "status": "1",
    "to": "0x35aac50f63e614e158f2f33aae23c6c50ec75785",
    "transactionHash": "0xe0d3f8695f9d105c0615f016655ba7a6875e99a532863e1abf07af40ca7413c8",
    "transactionIndex": "0"
}

```

Código JSON para documentación:

```javascript
curl --location 'https://u1my9uxwbm-u1bzt3mvmy-connect.us1-azure.kaleido.io/gateways/u1hudakhgw/0x35aac50f63e614e158f2f33aae23c6c50ec75785/registerPO?kld-from=0xf0afc19d9108b443096f0de4d461093b106b3bcd&kld-sync=true' \
--header 'Authorization: Basic dTFyNnIyZGxwczo5R1c4clJJbjNnaUR6akE3aVVKVVRwRHFsemVNdTM3V1ducm1PMkg4MlpJ' \
--header 'Content-Type: application/json' \
--data '{
  "POID": "5678"
}'

```

Registrar un step de la PO:

[![33](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/33.png?raw=true "33")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/33.png?raw=true "33")

Respuesta de POSTMAN:

```javascript
{
    "headers": {
        "id": "e8ca1392-b561-49fc-7552-20be822bb7cc",
        "type": "TransactionSuccess",
        "timeReceived": "2023-02-25T05:42:32.329395499Z",
        "timeElapsed": 5.297269067,
        "requestOffset": "",
        "requestId": "88b56300-ba5f-4eb7-6ca1-721d7668a546"
    },
    "blockHash": "0x140a3cce9ce8b6d4b74132a72ea7e27c44bdf5675b863be6df3c80df2f9e5013",
    "blockNumber": "79437",
    "cumulativeGasUsed": "82325",
    "from": "0xf0afc19d9108b443096f0de4d461093b106b3bcd",
    "gasUsed": "82325",
    "nonce": "0",
    "status": "1",
    "to": "0x35aac50f63e614e158f2f33aae23c6c50ec75785",
    "transactionHash": "0xd7c42afd117653e2bd1a2b993f67eacb1da03e64b5522b6697ffd706a4292603",
    "transactionIndex": "0"
}

```

Código JSON para documentación:

```javascript
curl --location 'https://u1my9uxwbm-u1bzt3mvmy-connect.us1-azure.kaleido.io/gateways/u1hudakhgw/0x35aac50f63e614e158f2f33aae23c6c50ec75785/registerStep?kld-from=0xf0afc19d9108b443096f0de4d461093b106b3bcd&kld-sync=true' \
--header 'Authorization: Basic dTFyNnIyZGxwczo5R1c4clJJbjNnaUR6akE3aVVKVVRwRHFsemVNdTM3V1ducm1PMkg4MlpJ' \
--header 'Content-Type: application/json' \
--data '{
  "POID": "5678",
  "metadata": "BOOKING_REQUEST OK"
}'

```

Validar status de PO:

[![34](https://github.com/rozoandrescamilo/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/34.png?raw=true "34")](https://github.com/Documentacion-de-la-API-REST-de-Kaleido-para-integracion-con-Frontend/blob/main/img/34.png?raw=true "34")

Respuesta de POSTMAN:

```javascript
{
    "metadata": "BOOKING_REQUEST OK",
    "status": "1"
}

```

Código JSON para documentación:

```javascript
curl --location 'https://u1my9uxwbm-u1bzt3mvmy-connect.us1-azure.kaleido.io/gateways/u1hudakhgw/0x35aac50f63e614e158f2f33aae23c6c50ec75785/POvalidator?kld-from=0xf0afc19d9108b443096f0de4d461093b106b3bcd&kld-sync=true' \
--header 'Authorization: Basic dTFyNnIyZGxwczo5R1c4clJJbjNnaUR6akE3aVVKVVRwRHFsemVNdTM3V1ducm1PMkg4MlpJ' \
--header 'Content-Type: application/json' \
--data '{
  "input": "5678",
  "input1": "1"
}'

```