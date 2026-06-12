---
title: "Problema con la configuración de la impresora en U-7.10"
date: 2007-10-13
forum: Colombia Team - Colombia
---

### Post by rcbonil on 2007-10-13
Hace una semana que tengo instalado Ubuntu 7.10 y el único problema que no he podido solucionar es con la configuración de la impresora y compartir la impresora a un portátil con windows, este último lo tenía bien en U-7.04, pero por esos días de ocio instale desde cero a Ubuntu 7.10 y desde hay no puedo imprimir desde el portátil.  Yo seguí los pasos que tengo en mi blog [http://installubuntu.blogspot.com/2007/10/cmo-compartir-una-impresora-conectada.html](http://installubuntu.blogspot.com/2007/10/cmo-compartir-una-impresora-conectada.html) pero nada

Y sobre la configuración el problema es que si voy hacer un cambio por ejemplo de calidad de impresión sale el siguiente mensaje "No autorizado: la contraseña puede estar incorrecta" y la cuestión es que yo no he introducido ninguna contraseña y cuando hago clic en el botón de Sistema/Administración/Impresora no me pide contraseña.

Y en "Parámetros del Servidor" me sale el siguiente error:
"Error del Servidor CUPS" "Un error se esta produciendo en la operación CUPS:  « Failed to set settings ».

El error_log me da lo siguiente:

D [13/Oct/2007:02:37:08 -0400] cupsdAcceptClient: 15 from localhost (Domain)
D [13/Oct/2007:02:37:09 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [13/Oct/2007:02:37:09 -0400] cupsdAuthorize: No authentication data provided.
D [13/Oct/2007:02:37:09 -0400] CUPS-Get-Printers
D [13/Oct/2007:02:37:09 -0400] cupsdProcessIPPRequest: 15 status_code=0 (successful-ok)
D [13/Oct/2007:02:37:09 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [13/Oct/2007:02:37:09 -0400] cupsdAuthorize: No authentication data provided.
D [13/Oct/2007:02:37:09 -0400] CUPS-Get-Classes
D [13/Oct/2007:02:37:09 -0400] cupsdProcessIPPRequest: 15 status_code=0 (successful-ok)
D [13/Oct/2007:02:37:09 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [13/Oct/2007:02:37:09 -0400] cupsdAuthorize: No authentication data provided.
D [13/Oct/2007:02:37:09 -0400] Get-Printer-Attributes ipp://localhost/printers/PDF
D [13/Oct/2007:02:37:09 -0400] cupsdProcessIPPRequest: 15 status_code=0 (successful-ok)
D [13/Oct/2007:02:37:09 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [13/Oct/2007:02:37:09 -0400] cupsdAuthorize: No authentication data provided.
D [13/Oct/2007:02:37:09 -0400] Get-Printer-Attributes ipp://localhost/printers/Stylus_CX4800
D [13/Oct/2007:02:37:09 -0400] cupsdProcessIPPRequest: 15 status_code=0 (successful-ok)
D [13/Oct/2007:02:37:10 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [13/Oct/2007:02:37:10 -0400] cupsdAuthorize: No authentication data provided.
D [13/Oct/2007:02:37:10 -0400] Get-Printer-Attributes ipp://localhost/printers/Stylus_CX4800
D [13/Oct/2007:02:37:10 -0400] cupsdProcessIPPRequest: 15 status_code=0 (successful-ok)
D [13/Oct/2007:02:37:10 -0400] cupsdReadClient: 15 GET /printers/Stylus_CX4800.ppd HTTP/1.1
D [13/Oct/2007:02:37:10 -0400] cupsdAuthorize: No authentication data provided.
D [13/Oct/2007:02:37:10 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [13/Oct/2007:02:37:10 -0400] cupsdAuthorize: No authentication data provided.
D [13/Oct/2007:02:37:10 -0400] Get-Jobs ipp://localhost/jobs/
D [13/Oct/2007:02:37:10 -0400] cupsdProcessIPPRequest: 15 status_code=0 (successful-ok)
D [13/Oct/2007:02:37:12 -0400] cupsdReadClient: 15 POST /admin/ HTTP/1.1
D [13/Oct/2007:02:37:12 -0400] cupsdAuthorize: No authentication data provided.
D [13/Oct/2007:02:37:12 -0400] CUPS-Set-Default ipp://localhost/printers/Stylus_CX4800
D [13/Oct/2007:02:37:12 -0400] cupsdIsAuthorized: username=""
E [13/Oct/2007:02:37:12 -0400] CUPS-Set-Default: Unauthorized
D [13/Oct/2007:02:37:12 -0400] cupsdSendError: 15 code=401 (Unauthorized)
D [13/Oct/2007:02:37:12 -0400] cupsdSendHeader: WWW-Authenticate: Negotiate

pero en este punto quedo totalmente perdido y en la siguiente página tienen algo similar: Ye he encontrado la siguiente solución: [https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/134503](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/134503)

Agradezco toda la ayuda que me puedan dar, ya que es lo único que me falta para que mi ubuntu sea totalmente perfecta.

---

