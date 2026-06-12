---
title: "Impossible to change usplash screen 9.04"
date: 2009-05-15
forum: General Help
---

### Post by mikflichy on 2009-05-15
Hola compañeros.
Pues eso. Tengo instalado el startup manager, el usplash, el usplash-dev.Al arrancar el administrador de arranque e intentar cambiar la pantalla de inicio por otra descargada de gnome-look no funciona. Me acepta el cambio, pero al reiniciar, me sale en la pantalla el código de arranque escrito, no grafico. 
Si vuelvo a poner el que tiene por defecto ubuntu me vuelve a funcionar correctamente.
A ver si me podeis orientar un poquito.
Gracias.

Hi friends.
I've installed the startup manager, usplash and usplash-dev. I change the usplash screen in starup manager/apparence for another usplash theme, downloaded of the gnome-look page but when i restart my computer, the screen shows the start code whith letters, no graphics.
If i change again the usplash screen for the default, everiting works correctly again.
Please, help me for change this.
Sorry for my englis.
Thanks a lot.

---

### Post by copjon on 2009-06-17
Having the same problem so..Bump!

---

### Post by QIII on 2009-06-17
Many usplash themes have not been updated by their authors for compatibility for Jaunty.  

That's why you get the verbose splash.

You might get lucky with something else.

I wouldn't count on them making any updates for Ubuntu, because Karmic will not use usplash any longer.

---

### Post by tom.swartz07 on 2009-08-10
Hi QIII et al,
Thanks for the tip.


Unfortunately, I was not aware of this fact before I started to try some usplash themes....
Now, all I could get is a fully verbose splash, and I cannot for the life of me figure out how to change it back to the default 'out-of-the-box' splash screen...

Does ANYONE know how to change it back to the default?

---

### Post by phishStix! on 2009-08-17
[FONT=Arial][SIZE=2]tom.swartz07 - 

     I had the same problem on my machine recently.  I use 9.04, and tried to change the usplash, but to no avail, I got a warning from grub, stating that I was attempting to use an unknown VGA mode, and to press ENTER, or SPACE; to change the video mode, or to simply continue.  My laptop (Gateway P-7801u FX) froze when I selected --ANY-- video mode (??), so I hit SPACE to continue.  This led me to the verbose startup screen.  It took me all day to reset my setup to use the 'out-of-the-box' usplash, and all I had to do was:
[SIZE=1]
   [/SIZE][/SIZE][/FONT][SIZE=1][FONT=Arial][SIZE=2][I][SIZE=1]sudo dpkg -r usplash usplash-theme-ubuntu
   sudo apt-get install usplash usplash-theme-ubuntu[/SIZE]
[/I][/SIZE][/FONT][SIZE=2][FONT=Arial]
    Alternatively, you can use Synaptic Package Manager.  Just search 'usplash', and uninstall [/FONT]usplash, and any usplash themes, and re-install them...    

                   Hope this helps,
                          Joe Jamison
[/SIZE][/SIZE]

---

### Post by phishStix! on 2009-08-17
My bad, forgot to mention that the usplash themes provided in Synaptic Package Manager seem to work for me...

(Just make sure that if you've added any non-jaunty repositories, that the usplash you select is from a Jaunty repo...)

---

### Post by tom.swartz07 on 2009-08-17
Thanks Joe!

Helped a lot!

---

