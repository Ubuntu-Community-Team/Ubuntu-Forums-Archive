---
title: "compiz effect not working and advanced desktop not listed..."
date: 2009-02-27
forum: General Help
---

### Post by creeper112 on 2009-02-27
Hello all,
 I'm really new to Ubuntu but I really think its a cool OS. I don't really know anything about it but by watching some youtube videos about it seem really cool how you can customize your desktop and other things as well. Im running Ubuntu 8.10 Intrepid on my Dell laptop Latitude.  My question is about getting the 3-D effect and fusion effect as well.  I read through a couple of threads and I did a check to see if compiz was compatible on my machine:

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


I believe this means yes.  I tried to access the Advanced Desktop under Systems/Preference, but it is not listed.  Am I doing anything wrong?  I have the Compizconfig settings manager but no advanced desktop.  Is there a tutorial on how to this because I'm a real newbie to this and would like to get to know Ubuntu a little better.  Thanks in advanced.

---

### Post by Lunx on 2009-02-27
To get it all working properly you need to go to **System --> Appearance --> Visual Effects** and make sure the bottom checkbox is selected, then you should be able to go to Compiz Settings Manager and enable desktopcube and all the other goodies

Hope that helps

---

### Post by Lunx on 2009-02-27
You can also install fusion icon to make it easy to select between Compiz and Metacity etc

Either go to synaptic and search for fusion-icon, or you can open a terminal and run

```
sudo apt-get install fusion-icon
```

Once you have that installed you can find it in **Applications -->System Tools**. Run it to put an icon on your panel that lets you select between window managers (sometimes other 3D apps don't play nicely with Compiz, so you can easily disable it this way)

---

### Post by creeper112 on 2009-02-27
thanks guys I will try it out.  Is there anything else i need to know?

---

### Post by Lunx on 2009-02-27
> **creeper112 said:**
> thanks guys I will try it out.  Is there anything else i need to know?

You can find a basic description of the desktop in chapter 3 of [[COLOR="Purple"]this guide[/COLOR]]("http://www.ubuntupocketguide.com/") (worth a look for a great intro to Ubuntu in general)

---

