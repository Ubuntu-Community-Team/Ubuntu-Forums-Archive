---
title: "Imposíbel abrir portos"
date: 2010-05-12
forum: Galician LoCo Team
---

### Post by rainbowgz on 2010-05-12
Ola, teño un problema, non son capaz de abrir os portos con ubuntu 10.04 (64bits). Instalei o firestarter, e tamen usei ufw, en ambos parece que os portos estan abertos, de feito cando escribo por liña de comandos en ufw diceme que xa estan activadas esas regras.

Pero logo non me saen, como se nada pasara. 

Estou desesperado, levo semanas buscando info e facendo cousas e nada


saudos...

---

### Post by felipexil on 2010-05-12
Boas rainbowgz!

Necesitaría mais detalles para poderche axudar:

En primeiro lugar un par de preguntas por precaución: a computadora na que queres abrir os portos para o servizo está detrás dun *router* ou está conectada directamente a Internet? tés abertos e redirixidos correctamente eses portos no *router*?

Se non estás detrás dun *router*:
[LIST]
[*]Que servizo queres abrir exactamente? Probaras a conectarte a ese servizo antes de instalar o "firestarter" ou o "ufw"? (se están desactivados, os portos deberían estar abertos).
[*]Poderías pegar o resultado de "iptables -L"?
[/LIST]

Saúdos!

---

### Post by rainbowgz on 2010-05-13
Ola, moitas grazas por contestar tan rápido e desculpa por non engadir toda a información necesaria para que me poidades axudar.

Teño router, as veces conéctome por dhpc e outra configuro eu a IP, nos dous casos sempre abro os portos a esas IP's, en Windows sempre me foi así (xa sei que isto non é windows). 

Conecteime ao Amule e dame id baixa, pero ademais cando fago: [http://www.internautas.org/w-scanonline.php](http://www.internautas.org/w-scanonline.php) dame que o porto esta fechado.

Buscando por Internte fixen o de UFW, pero nada, non pasa nada. Logo dixéronme que mirara o das iptables, e resulta que si están activadas (deben vir así de serie, uso ubuntu 10.04 64bits) entón instalei o Firestarter e aceptei esas conexións e nada. Reiniciei como 10 veces, volvín a facer todo como outras 10 veces.

Creo que me vou a suicidar. :(

Os portos que quero abrir son o 85 para TCP e 1985 para UDP

**RESULTADO DAS IPTABLES:**
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  host-200-40-42-2.easymail.net.uy  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  host-200-40-42-2.easymail.net.uy  anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             192.168.1.255       
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.3          host-200-40-42-2.easymail.net.uy tcp dpt:domain 
CCEPT     udp  --  192.168.1.3          host-200-40-42-2.easymail.net.uy udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:85 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:85 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:1985 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:1985 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            


Grazas!

---

### Post by felipexil on 2010-05-14
Non o mirei a fondo, pero apostaría a que o problema está nalgunha das regras que creou o Firestarter. Proba a desactivalas con:

sudo iptables -F INPUT
sudo iptables -F FORWARD
sudo iptables -F OUTPUT
sudo iptables -P INPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -X LOG_FILTER
sudo iptables -X LSI
sudo iptables -X LSO
sudo iptables -X OUTBOUND

---

### Post by rainbowgz on 2010-05-14
Ola, grazas unha vez máis por contestarme.

O acabo de facer, pero non todos os comandos me dan resposta, iso e boa sinal ou mala? Por certo, debería desinstalar o firewall de Firestarter, e instalar só a interfaz gráfica de UFW, porque se xa me da problemas así, se ando abrir nun lado e noutro, igual o fago pior, non?

saudos

---

### Post by rainbowgz on 2010-05-14
Xa o arranxei, despois de dar moitas voltas vou comentar como fixen:

Cando instalei o Amule traia uns portos por defecto, eu os mudei, os abrin no router e aínda así non iba, tiña id baixa, enton procurei info en internet e me dixeron que e das iptables o firewall que ven no kernel de ubuntu, para xestionalo instalei un xestor gráfico chamado FIRESTARTER, e configurei, non fixo nada, seguia sin poder, logo usei a liña de comandos con UFW e tampouco, decidin eliminar firestarter e antes pasar os comandos que ti me dixeches no post anterior, e instalei o xestor grafico de UFW que se chama GUFW, reiniciei, puxen os portos dende gufw e xa me vai.

Aqui tendes un tutorial: [http://sliceoflinux.com/2010/01/29/gufw-la-cara-amable-del-cortafuegos-preinstalado-en-ubuntu-9-10/](http://sliceoflinux.com/2010/01/29/gufw-la-cara-amable-del-cortafuegos-preinstalado-en-ubuntu-9-10/)


obrigado pola axuda :guitar:

---

### Post by felipexil on 2010-05-15
Alégrome de que xa che funcione todo, e grazas por poñer toda a información sobre a solución!.

---

### Post by leillo1975 on 2010-05-18
É bo sabelo.... gracias por publicar a solución

---

