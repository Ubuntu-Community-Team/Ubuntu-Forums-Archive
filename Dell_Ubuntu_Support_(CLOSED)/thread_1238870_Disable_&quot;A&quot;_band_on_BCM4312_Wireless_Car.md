---
title: "Disable &quot;A&quot; band on BCM4312 Wireless Card (Inspiron 1525)"
date: 2009-08-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sphm on 2009-08-12
Hello,

I'm running Ubuntu Jaunty on my Inspiron 1525 and the speakers are always buzzing and crackling. The Dell technical support told me to try to disable the "A" band from my wireless card (it supports a/b/g). I search the dell forums ans this problem is commom among dell laptops, but all post were abou windows and nothing about ubuntu.
As I bought this laptop with windows vista, Dell says that if I want full support I'll have to install Vista again with the default partions. For god sake this laptop has never runned windows and I'd like to keep it this way, but if it's really a hardware issue I'll have to install Visto to prove it, what will make me a lot of work.
**So please, how can I disable the "A" band of my wireless card??**


lspci
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

PS. Now I'm running the proprietary driver and the buzzes seems to be a little lower, but it's still there... anyway turn the wireless off don't make the sound completely desappear.

Olá,

Tenho um Dell Inspiron 1525 com uma placa wireless BCM4312, os falantes ficam fazendo chiados e zumbidos, o suporte da Dell recomendou que eu desativasse a banda "A" da placa wireless (visto que ela suporta a/n/g), pesquisei nos foruns da dell e essa solução parece ter funcionado para vários usuários, no entanto, todos os posts tratavam do Windows e nunca do linux.
Gostaria de saber, com urgência, como fazer isso, pois como comprei este computador com Windows Vista (infelizmente a Dell só vende este modelo com Ubuntu nos EUA e Alemanha) o fabricante disse que só trocará o hardware se o teste for feito com windows e ainda seguindo todos os passos estabelecidos por eles, fazendo com que eu tenha que apagar todas as minhas partições (uso apenas ubuntu, mas fiz uma particação para o /boot swap "/" e /home)

lspci
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

PS. Estou rodando Ubuntu 9.04, ja testei com os dois drivers disponíveis, livre e proprietário, ambos deram o mesmo problema.

---

