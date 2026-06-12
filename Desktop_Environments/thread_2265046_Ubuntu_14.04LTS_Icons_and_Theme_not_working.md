---
title: "Ubuntu 14.04LTS Icons and Theme not working"
date: 2015-02-12
forum: Desktop Environments
---

### Post by waleedgplus on 2015-02-12
Recently i've installed Ubuntu 14.04, works perfectly, but i tried to change the icons(Numix Circle) and theme(Numix, gtk i guess) with Unity Tweak tool. None of the installed themes or icons are working/changing. When i run compiz --replace in terminal, it brings all the changes i've made with the unity tweak tool and everything works perfectly, but on reboot theme and icons resets to default.

**After Rebooting**

[IMG]https://lh6.googleusercontent.com/-ky_Z5D4AU9g/VNxqnnvLm9I/AAAAAAAAKJU/jAl1RH8yxVU/w1597-h771-no/Capture2.JPG[/IMG]

[B]After Running compiz --replace 
[/B]
[IMG]https://lh5.googleusercontent.com/-pb2zlLdIprk/VNxqoZtWAaI/AAAAAAAAKJc/-eCnbMklpo8/w1598-h771-no/Capture3.JPG[/IMG]

[IMG]https://lh4.googleusercontent.com/-92DXj0FMEKw/VNxqnf3OG8I/AAAAAAAAKJQ/I_D9xU2hSYQ/w1598-h770-no/Capture.JPG[/IMG]

---

### Post by kerry_s on 2015-02-12
have you tried adding "compiz --replace" to startup apps ?

---

### Post by waleedgplus on 2015-02-12
No, how can i do that?

---

### Post by Frogs Hair on 2015-02-12
I've never needed to use the compiz --replace command to enable 3rd party themes or icons so you may want to start with a compiz reset command first. 

If not already installed : ```
 sudo apt-get install dconf-tools
``` Reset Compiz: ```
dconf reset -f /org/compiz/
```

---

### Post by waleedgplus on 2015-02-13
dconf reset -f /org/compiz/
It didn't help, the problem still persist. Here's what works, when i try to logout and wait for exactly half a minute and log back in, it brings all the changes back to normal without compiz --replace. Any ideas what's happening here?

---

### Post by kerry_s on 2015-02-13
was compiz installed by default ? i thought unity used mutter ?

---

### Post by waleedgplus on 2015-02-13
I didn't install it, so i guess it was installed by default.

---

### Post by Frogs Hair on 2015-02-13
The Gnome Shell uses Mutter and Unity is Compiz based. You could try reseting unity next.```
 setsid unity
```

---

