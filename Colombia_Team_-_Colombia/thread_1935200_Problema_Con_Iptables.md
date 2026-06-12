---
title: "Problema Con Iptables"
date: 2012-03-03
forum: Colombia Team - Colombia
---

### Post by sistemasCIAF on 2012-03-03
Buenas tardes amigos

en estos momento tengo un servidor en ubuntu 8.4, esta configurado con squid para que me haga filtrado de paginas a una red local, pero tengo un inconveniente, las paginas que abren por protocolos https, entre otros el no las permite abrir, y otro inconveniente es que las personas que usan outlook en la red o otro gestor de correos no les permite sincronizar su bandeja de entrada, en estos momentos quiero que por este servidor pasen las peticiones de los puertos de outlook que son:

25 110  143  993 995 

también e escuchado que por medio de iptables puedo hacer que mi squid escuche peticiones por el puerto 80 21 443 entre otros, y las redirija al puerto 3128 que fue el que le habilite para trabajar

ya e probado infinidad de reglas de iptables que e encontrado en diferentes foros, sin resultados positivos.

quiero saber si debo cambiar mi distribución o mi vercion de ubuntu, y cual me recomendarían para que me funcione como servidor proxy

Muchas gracias por su atención

Cesar Blandon
Auxiliar de sistemas
Univercidad CIAF Pereira

---

### Post by sistemasCIAF on 2012-03-07
Buenos Días 
agrego las reglas que tengo funcionando con el Iptables, pero que no me funcionan por si alguien me puede colaborar

Bueno les cuento tengo un archivo en la carpeta init.d con nombre iptables.cf con el siguiente contenido:
_____________________________________
#!/bin/sh
##SCRIPT DE IPTABLEs
echo -n Aplicando reglas de Firewall
## FLUSH DE REGLAS

iptables -F
iptables -X
iptables -Z
iptables -t nat -F

#HABILITAR FORWARD DE PAQUETES
iptables -t nat -a POSTROUNTING -o -i eth1 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward

##SE ESTABLECEN POLITICAS POR DEFECTO
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -t nat -P PREROUTING ACCEPT
iptables -t nat -P POSTROUTING ACCEPT

## EMPIEZA EL FILTRADO, eth0 es la salida a internet, eth1 la salida a red local

#El localhost se deja abierto
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

#Abrimos el puerto del Ftp
iptables -A OUTUT -p tcp --dport 21 -j ACCEPT
iptables -A INPUT -p tcp --sport 21 -j ACCEPT

#Abrimos el puerto del WEb, PUERTO 80
iptables -A INPUT -i eth1 -p tcp --sport 80 -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --dport 80 -j ACCEPT

#Abrimos el puerto del WEbmin, PUERTO 10000
iptables -A INPUT -i eth1 -p tcp --sport 10000 -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --dport 10000 -j ACCEPT

#PERMITIR LA SALIDA SMTP, PUERTO 25 DEL CORREO
iptables -A INPUT -i eth0 -p tcp --sport 25 -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --dport 25 -j ACCEPT
#SMTP
iptables -A INPUT -s 0.0.0.0/0 -p tcp --dport 25 -j ACCEPT
#POP3
iptables -A INPUT -s 0.0.0.0/0 -p tcp --dport 110 -j ACCEPT

#Dejamos abierto el acceso al firewall desde la red local
iptables -A INPUT -s 192.168.0.0/24 -i eth1 -j ACCEPT

#Hacemos enmascaramiento de la red local y activamos el bit de FORWARDING
iptables -t nat -A POSTROUTING -s 192.168.0.0/24 -o eth0 -j MASQUERADE
iptables --table nat --append POSTROUTING --out-interface eth0 -j MASQUERADE

#REDIRECCIONO LA INFO A UN PUERTO, TRANSPARENCIA
iptables -t nat -A PREROUTING -i eth1 -s 192.168.0.0/24 -d ! 192.168.0.0/24 -p tcp --dport 80 -j REDIRECT --to-port 3128
echo *OK, verifiquese el script con iptables -L -n*
#FIN DEL SCRIPT
__________________________________________________ __

anteriormente tenia otro con este otro contenido 

__________________________________________________ __
#!/bin/sh
echo -n Aplicando Reglas de Firewall...
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 21 -j REDIRECT --to-port 3128
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 443 -j REDIRECT --to-port 3128
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P INPUT ACCEPT
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables --table nat --append POSTROUTING --out-interface eth1 -j MASQUERADE
iptables --append FORWARD --in-interface eth0 -j ACCEPT
iptables -A INPUT -s 0.0.0.0/0 -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -s 0.0.0.0/0 -p tcp --dport 21 -j ACCEPT
iptables -A INPUT -s 0.0.0.0/0 -p tcp --dport 25 -j ACCEPT
iptables -A INPUT -s 0.0.0.0/0 -p tcp --dport 110 -j ACCEPT
iptables -A INPUT -s 0.0.0.0/0 -p tcp --dport 995 -j ACCEPT
iptables -A INPUT -s 0.0.0.0/0 -p tcp --dport 587 -j ACCEPT
iptables -A INPUT -s 0.0.0.0/0 -p tcp --dport 443 -j ACCEPT
iptables -A INPUT -s 0.0.0.0/0 -p tcp --dport 3128 -j ACCEPT
iptables -A FORWARD -s 190.145.50.33/29 -i eth0 -p tcp --dport 80 -j ACCEPT
iptables -A FORWARD -s 190.145.50.33/29 -i eth0 -p tcp --dport 21 -j ACCEPT
iptables -A FORWARD -s 190.145.50.33/29 -i eth0 -p tcp --dport 25 -j ACCEPT
iptables -A FORWARD -s 190.145.50.33/29 -i eth0 -p tcp --dport 443 -j ACCEPT
iptables -A FORWARD -s 190.145.50.33/29 -i eth0 -p tcp --dport 587 -j ACCEPT
iptables -A FORWARD -s 190.145.50.33/29 -i eth0 -p tcp --dport 3128 -j ACCEPT
iptables -A FORWARD -s 190.145.50.33/29 -i eth0 -p udp --dport 110 -j ACCEPT
iptables -A FORWARD -s 190.145.50.33/29 -i eth0 -p udp --dport 995 -j ACCEPT
iptables -F
iptables -X
iptables -Z
iptables -t nat -F
iptables -t nat -P PREROUTING ACCEPT
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -A FORWARD -p tcp --dport 80 -j ACCEPT
iptables -A FORWARD -p tcp --sport 80 -j ACCEPT
iptables -A FORWARD -p tcp --sport 21 -j ACCEPT
iptables -A FORWARD -p tcp --dport 21 -j ACCEPT
iptables -A FORWARD -p tcp --dport 25 -j ACCEPT
iptables -A FORWARD -p tcp --sport 25 -j ACCEPT
iptables -A FORWARD -p tcp --dport 110 -j ACCEPT
iptables -A FORWARD -p tcp --sport 110 -j ACCEPT 
iptables -A FORWARD -p tcp --dport 995 -j ACCEPT
iptables -A FORWARD -p tcp --sport 995 -j ACCEPT
iptables -A FORWARD -p tcp --dport 587 -j ACCEPT
iptables -A FORWARD -p tcp --sport 587 -j ACCEPT
iptables -A FORWARD -p tcp --sport 443 -j ACCEPT
iptables -A FORWARD -p tcp --dport 443 -j ACCEPT
iptables -A FORWARD -p tcp --dport 3128 -j ACCEPT
iptables -A FORWARD -p tcp --sport 3128 -j ACCEPT
echo " OK . Verifique que lo que se aplica con: iptables -L -n"

# Fin del script

__________________________________________________ _________

en el squid solo e configurado esto, aparte de las acl´s y las http_access

# Squid normally listens to port 3128
http_port 3128 transparent

#Default:
cache_dir ufs /var/spool/squid 1000 16 256
__________________________________________________ ____

tengo una versión squid 2.6 stable18
y ubuntu 8.4

muchas gracias en lo que me puedan colaborar
pero ya estoy pensando en comprar mas maquina y actualizar el ubuntua uno mas reciente

---

