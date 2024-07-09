Pikaday (fork)
========


## Intro

Este repo parte de un fork de la librería https://github.com/Pikaday/Pikaday y se ha extendido su funcionalidad para poder adaptar la librería a las nuevas funcionalidades de zityhub.

El repo consta de dos remotes: 

- `upstream`: Hace referencia al repositorio original de pikaday (Pikaday/Pikaday)
- `origin`: Hace referencia al repositorio actual del fork de pikaday de zityhub (zityhub/Pikaday)

## Desarrollando en local

Para añadir nuevas funcionalidades el proceso de creación de ramas sería el mismo que se utiliza en zityhub para cualquier proyecto.

Para poder probar los nuevos cambios introducidos hay dos maneras:

- Uso de `yarn link`: Creación de un link simbólico del repo actual y posterior uso en el proyecto donde se necesite (ej: booking app) con `yarn link "pikaday"`. Es importante que una vez se finalicen las pruebas se haga el `yarn unlink`.
- Hacer referencia en el `package.json` del proyecto donde se necesite usar a la rama en concreto que contiene la nueva funcionalidad. Sería algo así como:
```
"pikaday": "zityhub/Pikaday#feat/BOOK-XXXX_bla-bla",
```

## Versionado

Inicialmente al hacer el fork se heredaron los tags del repo original. Estos fueron eliminados para poder empezar a versionar de cero.

El proceso utilizado para el versionado es hacerlo manualmente con los siguientes pasos:

1. Actualizar `package.json` con la nueva `"version"` y hacer commit y push
2. Generar el nuevo tag con `git tag vX.X.X` ej: (`git tag v0.1.0`)
3. Pushear tag con `git push origin vX.X.X`
4. Actualizar `package.json` en el proyecto donde se quiere consumir este proyecto con: `"pikaday": "zityhub/Pikaday#vX.X.X"` y hacer un `yarn`

*** OJO es importante tener en cuenta que si en algún momento se hiciese una sincronización con la rama master del repo original habría que evitar que se sincronizasen los tags porque sino habría colisión con los del proyecto actual. Para ello habría que utilizar:
```
git fetch upstream --no-tags
```