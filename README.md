# dicas
Resumo de links e dicas para uso no dia a dia


## regex
 ### de bolso ([fonte](https://www.alura.com.br/artigos/javascript-replace-manipulando-strings-e-regex))
 	
 + [referência rápida](https://www.regular-expressions.info/refquick.html)
   
_____
## JS
 ### date format
+ https://github.com/you-dont-need/You-Dont-Need-Momentjs
	
_____
## jest mocks
#### classe com construtor e método assíncrono

  ClasseExemplo.ts
  ```javascript
  import ClasseMockar from '../ClasseMockar';

class ClasseTestar {
  classeMockar: ClasseMockar;

  constructor() {
    this.classeMockar = new ClasseMockar();
  }

  public async metodoTestar(): Promise<string> {
    try {
      const resposta: string = await
      this.classeMockar.metodoMockar('xpto');

      if (!resposta) {
        throw new Error('Erro ao recuperar dado');
      }
      return resposta;
    } catch (e) {
      throw e;
    }
  }
}

export default ClasseTestar;
```
  
  Mock exemplo
```javascript
const ClasseMockar = require('../../src/ClasseMockar');
let mockRetornarErro = false;
jest.mock('../../src/ClasseMockar', () => jest.fn());

ClasseMockar.mockImplementation(() => ({
  metodoMockar: jest.fn(async function (args: string) {
    return mockRetornarErro
           ?  Promise.reject(new Error('Erro ao recuperar dado'))
           :  Promise.resolve('Retorno válido');
  })
}));
```

  Exemplo de uso
```javascript
describe("Validar metodoTestar", () => {
  beforeEach(() => {
     // inicialize o que precisar
  })

  test('Erro ao acessar obter retorno da funcionalidade ', async () => {
    try {
      mockRetornarErro = true;
      let result = await classeTestar.metodoTestar('argumento(s)');
      expect(result).not.toBeDefined();
    } catch (error) {
      expect(error).toBeDefined();
      expect(error).toEqual('Não foi possível obter dados');
    }
  });
  ```
  
  #### mock 'request'
  ```javascript
  //mock request
let mockRequestOptions = undefined;
let mockRequestError = { code: 'ETIMEDOUT', message: 'Erro do ETIMEDOUT' };
let mockRequestResponse = {};

jest.mock('request', () => {
  const post = jest.fn((mockRequestOptions, cb) => {
    cb(mockRequestError, mockRequestResponse)
  });
  return { post };
});
```

## typescript

### generators
  + (Generators, yelds, iterators...)[https://braziljs.org/artigos/generators-yield-e-iterators/]


_____
[Git Hub MD tips](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#code)
[Referência rápida](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#code)


## java

### Response
   + **GET** exemplo de uso:
   ```java
   Response response = client
                    .target(urlString)
                    .queryParam("parâmetro", valor_parâmetro)
                    .path(path)
                    .request(MediaType.APPLICATION_JSON_TYPE)
                    .get();
```
   + **POST** exemplo de uso
   ```java
   Response response = client.target(baseUrl)
                    .path(ENDPOINT_LOG_EXECUCAO_GRAVAR)
                    .request(MediaType.APPLICATION_JSON)
                    .post(Entity.entity(logExecucao, "application/json; charset=UTF-8"));
```
