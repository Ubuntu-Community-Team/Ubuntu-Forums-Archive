---
title: "GTK engines- wtf"
date: 2008-01-23
forum: Desktop Effects &amp; Customization
---

### Post by Fraser from Scotland on 2008-01-23
I want to install this theme [http://www.gnome-look.org/content/show.php/Murrina+Relax?content=54250](http://www.gnome-look.org/content/show.php/Murrina+Relax?content=54250)
 and it says I need this gtk engine [http://murrine.netsons.org/index.php?q=node/5](http://murrine.netsons.org/index.php?q=node/5)  so i downloaded it and i have no idea what to do with it. In the installation help it says:  Using Binary Packages:

    * Ubuntu:

Murrine is in Universe! Check out feisty repository! 

I dont know what that is or how to do it. Please help, all i want is a little bit of custimisation without too much hassle- and too much hassle is what this is becoming :(

---

### Post by VictorR on 2008-01-24
This just means that you can install it using Synaptic:
1. menu System -> Administration -> Synaptic Package Manager
2. click Search
3. type "murrine"  (no quotes) and click Search
4. select gtk2-engines-murrine for installation, click Apply and enjoy

Universe is the name of one of main Ubuntu repositories.

Another way (shorter):
in the terminal type
```
sudo apt-get install gtk2-engines-murrine

```

---

