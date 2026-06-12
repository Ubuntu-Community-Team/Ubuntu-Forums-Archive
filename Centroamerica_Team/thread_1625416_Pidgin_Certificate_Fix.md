---
title: "Pidgin Certificate Fix"
date: 2010-11-19
forum: Centroamerica Team
---

### Post by srlinux on 2010-11-19
Hola algunos tendran problemas con el certificado ssl al intentar entrar al pidgin esta es la solucion:

```
rm .purple/certificates/x509/tls_peers/omega.contacts.msn.com && cd .purple/certificates/x509/tls_peers/ && wget http://dl.dropbox.com/u/321718/omega.contacts.msn.com 
```

con este comando borramos el archivo omega.contacts.msn.com entramos al directorio y descargamos el nuevo omega.contacts.msn.com que es el que funciona .

Descargamos estos archivos luego descomprimir y copiamos en el directorio /usr/share/purple/ca-certs

[ATTACH]175982[/ATTACH]
[ATTACH]175983[/ATTACH]
[ATTACH]175984[/ATTACH]

```
sudo nautilus /usr/share/purple/ca-certs
```



reiniciar el pidgin y listo..:P

---

### Post by mama21mama on 2010-11-19
también hay un script dando vueltas.
que lo e probado y realmente funciona.

```
#!/bin/bash

# save this script in ~/bin/ssl_update
# add domain names as you need them

servers=(omega.contacts.msn.com blah.dot.com)

for server in "${servers[@]}"; do
    echo | openssl s_client -connect "$server":443 2>&1 | \
    sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' \
    > "$HOME/.purple/certificates/x509/tls_peers/$server"
done
```

[Fuente]("http://paste.ubuntu.com/534121/")

va un mate amargo, saludos.

Edito: bueno esta funciona si no tienes privilegios para hacer lo de arriba.

---

