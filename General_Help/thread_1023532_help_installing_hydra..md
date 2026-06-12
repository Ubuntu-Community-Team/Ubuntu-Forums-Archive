---
title: "help installing hydra."
date: 2008-12-28
forum: General Help
---

### Post by Isilion on 2008-12-28
hi. im trying to install hydra. i downloaded source from [http://www.0xbadc0de.be](http://www.0xbadc0de.be) and when i type make i get this output:

isilion@isilion:~/Escritorio/hydra-5.4-src$ make
gcc -I. -Wall -O2 -c hydra-ssh2.c -DLIBPOSTGRES -DLIBSSH 
hydra-ssh2.c:10:2: aviso: #warning "If compilation of hydra-ssh2 fails, you are not using v0.11. Download from http://www.0xbadc0de.be/"
hydra-ssh2.c: En la función ‘start_ssh2’:
hydra-ssh2.c:34: aviso: declaración implícita de la función ‘options_new’
hydra-ssh2.c:34: aviso: la asignación crea un puntero desde un entero sin una conversión
hydra-ssh2.c:44: aviso: declaración implícita de la función ‘options_set_wanted_method’
hydra-ssh2.c:44: error: ‘KEX_COMP_C_S’ no se declaró aquí (primer uso en esta función)
hydra-ssh2.c:44: error: (Cada identificador no declarado solamente se reporta una vez
hydra-ssh2.c:44: error: para cada funcion en la que aparece.)
hydra-ssh2.c:45: error: ‘KEX_COMP_S_C’ no se declaró aquí (primer uso en esta función)
hydra-ssh2.c:46: aviso: declaración implícita de la función ‘options_set_port’
hydra-ssh2.c:47: aviso: declaración implícita de la función ‘options_set_host’
hydra-ssh2.c:48: aviso: declaración implícita de la función ‘options_set_username’
hydra-ssh2.c:50: aviso: se pasa el argumento 1 de ‘ssh_connect’ desde un tipo de puntero incompatible
hydra-ssh2.c:50: aviso: la asignación crea un puntero desde un entero sin una conversión
hydra-ssh2.c:82: aviso: declaración implícita de la función ‘ssh_error_code’
make: *** [hydra-ssh2.o] Error 1

im sure i make before libssh v 0.11 from that page, but i still getting this error. seems like a lib is missing, not? please help. thanks3

---

