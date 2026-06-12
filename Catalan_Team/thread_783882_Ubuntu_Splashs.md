---
title: "Ubuntu Splashs"
date: 2008-05-06
forum: Catalan Team
---

### Post by LitusMayol on 2008-05-06
Bones a tots i totes!

A veure... Us explico. 


Jo vaig començar amb Kubuntu. I després de la decepció que em vaig emportar amb el KDE4 i que tenia el 3.5.8 rebentat per potinejar-lo amb Compiz i companyia em vaig passar a GNOME. Ara estic utilitzant Ubuntu i he intentat netejar-ho tot. He desinstal·lat el KDE i el Kdm. Però quan engego l'ordinador encara em surt el símbol de Kubuntu i la barra blava omplint-se. 

Voldria posar el de Ubuntu. Algú em pot ajudar?


Merci familia!

---

### Post by CarlesOriol on 2008-05-06
Amb permis dels kdistes habituals:

sudo update-alternatives --config usplash-artwork.so


Seleccionarem la pantalla d&#8217;inici.

I l&#8217;activarem amb:

sudo dpkg-reconfigure usplash

---

### Post by crazyserver on 2008-05-06
Mestre!
```
sudo apt-get install usplash-theme-ubuntu
sudo apt-get remove kubuntu-artwork-usplash
```

I per si no se't canvia... i et quedes sense...XD
```
sudo aptitude reinstall usplash
```


EDITO: El carlesoriol se m'ha adelantat i segur que es mes maca la seva manera...

---

### Post by LitusMayol on 2008-05-06
A veure senyors: 
```

litus@mayolets:~$ sudo update-alternatives --config usplash-artwork.so
[sudo] password for litus: 

Hi ha 3 alternatives que proveeixin «usplash-artwork.so».

  Selecció     Alternativa
-----------------------------------------------
          1    /usr/lib/usplash/usplash-theme-ubuntu.so
*+        2    /usr/lib/usplash/usplash-theme-kubuntu.so
          3    /usr/lib/usplash/ubuntustudio-theme.so

Premeu retorn per a mantenir l'opció per defecte[*], o introduïu un número de selecció: 1
Using '/usr/lib/usplash/usplash-theme-ubuntu.so' to provide 'usplash-artwork.so'.
litus@mayolets:~$ 
```


Ara no puc reiniciar l'ordinador, estic fent cosetes més aviat importants. Després el reinicio i us dic què. 

Merci als dos! ;) 


(PD: em fa una por la familia Oriol...! :P )

---

### Post by CarlesOriol on 2008-05-06
Et falta 

sudo dpkg-reconfigure usplash


(PD: em fa una por la familia Mayol...! :P )

---

### Post by LitusMayol on 2008-05-06
Fantàstic! ;) 

Merci a tots! (ja funciona!)

PD -Edit-: algú el pot posar com a SOLVED es que no puc... No hauria d'estar a "Thread Tools"

---

