---
title: "Tutorial: Setting up COMPIZ On KUBUNTU GUTSY (Exclusive HP  TX1000)"
date: 2008-01-01
forum: Desktop Effects &amp; Customization
---

### Post by netvampire on 2008-01-01
Hello,
I have kubuntu installed on an HP  tx1000. For the Tx1000 to perform correctly it was quite a headache to configure the touch screen, wifi, audio, boot parameters, etc....Well after all of that I was still determined to get Compiz working on this notebook. 

Finally its set up, and for those that are interested my steps are as follows. Please bare with me as this is the first tutorial i have ever written.

Preconditions:
A working tx1000 notebook running kubuntu


**We first start by configuring the graphics card with some new drivers.**

1) Download Envy package from 

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

2) I shut down the xserver
```
 /etc/init.d/kdm stop  
```

3) run envy as follows

```
 
cd path_to_envy's_deb_package
sudo dpkg -i envy*.deb
sudo apt-get install -f
sudo envy -t
 
```

4) Follow on screen instructions (Select Install NVIDIA Graphics Card)


**Install Compiz**

1) For compiz i  followed this guide located here to the 'T'.

[http://ubuntuforums.org/showthread.php?t=601310&page=7]("http://ubuntuforums.org/showthread.php?t=601310&page=1")

**Note: After the guide completed I still had a problem of having the menus for each window disappear. I fixed that as follows:**

2) open up a command window and type

```
 sudo apt-get install compiz  
```

3) in a command window type 
```
  gtk-window-decorator  
```

that should fix the disappearing menu borders. Good luck everyone I hope this guide works for you. Any questions feel free to ask. I am a newb when It comes to ubuntu but I will do my best to help.

---

### Post by K.Mandla on 2008-01-01
Moved to Desktop Effects and Customization.

---

