[TOC]

# Introducción

El presente documento tiene como finalidad guiarle en el proceso de actualización de los siguientes sitios de la **Coordinación de Educación en Salud** basados en Drupal:

- [Revista de Enfermería](http://revistaenfermeria.imss.gob.mx)
- [Revista Médica](http://revistamedica.imss.gob.mx)
- [Sitio de la División de Innovación Educativa](http://innovacioneducativa.imss.gob.mx)

Se explica paso a paso el proceso de actualización dentro de un ambiente virtual previamente configurado mismo que será copiado en una memoria USB de su propiedad, fuera de este ambiente requerirá configurar un sistema operativo Centos 7 con todo lo necesario para poder actualizar los sitios, dicha explicación se encuentra fuera de los alcances de este manual.

Para mantener el hilo de lo ocurrido con este proceso llámense dudas, errores, le sugiero colocarlas 
en [issues](https://github.com/ocerecedo/imss-actualizacion-sitios-drupal/issues), el cual es el canal de información oficial.

## Requerimientos

| Nombre                                      | Descripción                                                  |
| ------------------------------------------- | ------------------------------------------------------------ |
| [VMware Workstation](http://bit.ly/31VnOtl) | Aplicación para virtualizar sistemas operativos.             |
| Máquina Virtual                             | Contiene todo lo requerido para la actualización de los sitios. |
| Respaldos de Sitios                         | Última copia de los sitios en productivo.                    |

# VMware Workstation

VMware Workstation es un hipervisor alojado que se ejecuta en versiones x64 de los sistemas operativos Windows y Linux; permite a los usuarios configurar máquinas virtuales en una sola máquina física y usarlas simultáneamente junto con la máquina real.

## Instalación

Para instalar VMware Workstation realice los siguientes pasos:

1. Descargar la aplicación desde el sitio oficial proporcionado en la tabla de arriba

2. De clic sobre el ejecutable para iniciar el proceso de instalación y en la pantalla presione Next

3. Acepte los términos de la licencia y de clic en Next

4. Habilite "Enhanced Keyboard Driver" y de clic en Next

5. En las siguientes pantallas presione Next

6. Presione Install para comenzar

7. Presione finalizar y de clic en Restart

## Ejecutando la máquina virtual

En su memoria USB puede encontrar la máquina virtual con el nombre de **imagen_OVF_Revistas.rar**, una vez descomprimido el archivo rar, visualizará la siguiente estructura de ficheros:

- Revistas.mf
- Revistas.ovf
- Revistas-disk1.vmdk
- Revistas-file1.iso

Proceda a ejecutar el archivo llamado Revistas.ovf, la pantalla inmediata debe ser la siguiente:

![Importando m](C:\Users\nuxbaster\Documents\imss-actualizacion-sitios-drupal\docs\source\_static\import_Virtual_Machine.png)

Coloque el nombre y la ruta de su máquina virtual y proceda a dar clic en **Import**. Si después de dar clic en **Import**, le arroja un mensaje como el de la imagen siguiente, solo de clic en **Retry**

![Error al importar la máquina virtual](C:\Users\nuxbaster\Documents\imss-actualizacion-sitios-drupal\docs\source\_static\error_Import_Virtual_Machine.png)

Este proceso puede tomar varios minutos en completarse.

## Revisando la conectividad de la máquina virtual

Al finalizar el proceso anterior procedemos a iniciar la máquina virtual, las claves de acceso son las siguientes:

- **usuario: root** 
- **contraseña: toor** 

Una vez iniciada, observará lo siguiente donde debe colocar sus accesos:

![Iniciando la máquina virtual](C:\Users\nuxbaster\Documents\imss-actualizacion-sitios-drupal\docs\source\_static\iniciando_VM.png)

Dentro de la Shell, comprobaremos la conectividad de nuestra máquina virtual con el siguiente comando **ifconfig** si todo es correcto nos devolverá una dirección IP similar a como puede ver en la imagen:

![IP de la máquina virtual](C:\Users\nuxbaster\Documents\imss-actualizacion-sitios-drupal\docs\source\_static\ip_VM.png)

Tener una dirección IP asignada es **fundamental** para este proceso, ya que mediante esa IP podrá acceder vía navegador Web a nuestros sitios, si en el proceso anterior no le ha asignado una dirección IP, ejecute lo siguiente en su consola:

```bash
nmtui
```

