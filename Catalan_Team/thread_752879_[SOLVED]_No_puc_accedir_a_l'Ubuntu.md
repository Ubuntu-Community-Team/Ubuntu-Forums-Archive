---
title: "[SOLVED] No puc accedir a l'Ubuntu"
date: 2008-04-12
forum: Catalan Team
---

### Post by lluisalguero on 2008-04-12
Hola nois,
tinc un greu problema...l'Ubuntu no va, us explico el que he fet...

Voltant per Internet, vaig trobar que era posible actualitzar ja a la beta del 8.04 i seguint un tutorial, vaig ficar-me "manos a la obra".

Tot anava com la seda, fins que es va penja el portàtil..:(. Obviament cap combinació de tecles feia que allò tornés a la vida, fins i tot el vaig deixar una estona a veure si per si sol tornava a refer-se. La qüestió que finalment vaig tirar pel dret i el vaig parar per mig del botó de posta en marxa.

El torno a ficar en marxa, em surt la pantalleta del logo de l'Ubuntu i la barra com tal va carregant coses...i quan acaba, surt la pantalla en negre, el cursor parpadejant dalt de tot a l'esquerra...i ja està..sense poder fer res més...ni escriure texte ni res...

Torno a resetejar i ara ho provo amb el "recovery mode", em va sortint una llista del que (suposo) va carregant i al final torno a ser al mateix lloc, cursor parpadejant i ja està...

Suposo que ficant un live cd i tocant alguna coseta, serà posible tornar-lo a la vida, i es per això que us demano la vostra ajuda.

Moltes gràcies,
Lluís

---

### Post by patrickfromspain on 2008-04-12
el que podries provar es entrar amb el chroot. T'explico més o menys com va:

Arranques el cd live i obres un terminal i fas el següent:

```

sudo mkdir /media/ubuntu        #crees una carpeta on muntar el teu ubuntu instalat
sudo mount -t ext3 /dev/sdX /media/ubuntu      #On /dev/sdX es la particio on tens insta&#322;lat l'ubuntu. El muntes a /media ubuntu
sudo chroot /media/ubuntu     #entres a l'ubuntu insta&#322;lat via terminal, per via chroot. Les comandes a partir d'ara les hi estas donant a l'ubuntu insta&#322;lat.
apt-get update
apt-get dist-upgrade       #el deixes acabar i ho repeteixes 2 cops per si acàs

```

Ara ja pots reiniciar, a veure si això ha funcionat.

Salut!

---

### Post by lluisalguero on 2008-04-12
gràcies patrick pel consell

a la nit ho provaré i ja us diré com m'anat

---

### Post by lluisalguero on 2008-04-12
M'acabo de quedar de pasta de boniato...

Quan he arribat i mentre sopava li comentava a la parenta lo del ubuntu i m'ha mirat en cara extranya, va i em diu...però si funciona!! que aquesta tarda l'he fet anar !!

Efectivament...l'ubunut a tornat tot sol a la vida, sense fer-li res...

Deixo el tema com a solventat...gràcies patrick

---

