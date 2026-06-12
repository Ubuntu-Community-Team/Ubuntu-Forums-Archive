---
title: "Open Office menu bar"
date: 2008-12-31
forum: General Help
---

### Post by kidguayas on 2008-12-31
I have installed Intrepid Ibex on my laptop and Open Office 2.4 is the default.  When I open Open Office (OO) the menu bar does not show there. Does any one know why and how to fix it??? I am attaching a screen shot so you know what I mean...

Thanks,

kidguayas

---

### Post by fooman on 2008-12-31
might be a compiz issue....do you have compizconfig settings manager installed?

if not install it from synaptic,  or in a terminal:

```
sudo apt-get install compizconfig-settings-manager
```

open ccsm from system > preferences > compizconfig settings manager

when it opens, find "utility" on the left and click it.  you should see "workarounds" on the right...double click it.

try unchecking "legacy fullscreen support"....see if that helps.

---

### Post by kidguayas on 2008-12-31
Thanks for your help. This is not working. Any other ideas???

---

### Post by Tom--d on 2008-12-31
That could be compiz. Check Workarounds in Compiz Config and make sure OpenOffice is checked.

OR

It could be your theme.

---

### Post by kidguayas on 2008-12-31
I have tried all the different themes in Ibex but I still have the same problems and in compiz Open Office is check..Any more ideas for this problems

Thank you guys...

---

### Post by vanadium on 2008-12-31
Can you try the following: edit the file /etc/rc.local, add the line "export SAL_DISABLE_CAIROTEXT=1" and reboot the machine.

```

sudo gedit /etc/rc.local

```

Before the last line (exit 0), add the line "export SAL_DISABLE_CAIROTEXT=1"

My file looks like this at the end:

```

# Fix wrong animation OOo
export SAL_DISABLE_CAIROTEXT=1
exit 0

```

I did not have your issue, but had an issue with Impress. I think I read that that line would also correct the "invisible" menu as well. So just try it. If it does not work, just remove that line again. By the way, I am using Hardy, you might be using Intrepid. [edit] Indeed, you mentioned so.

---

### Post by DJ_Peng on 2008-12-31
I've seen this in several apps. What type of video card do you have in your system? If you use an Nvidia card (or chips) you may want to make sure you have the latest version drivers. There's a known issue in the Nvidia drivers that causes things like this.

WINE apps (and apps that use WINE like Picasa 3) require some extra tweaking but I haven't had problems with OOo since I got the latest drivers.

---

### Post by kidguayas on 2008-12-31
I have an NVidia graphics card. How can I update ? or where can I go?

Thanks,

kidguayas

---

### Post by Mze on 2008-12-31
Disable desktop effects for now..

System>>>Preferences>>>Appearance>>Visual Effects : Select "None"

---

### Post by abn91c on 2008-12-31
to fix you problem remove this file [COLOR="Blue"]**sudo apt-get remove openoffice.org-gnome**[/COLOR]

---

### Post by kidguayas on 2008-12-31
It did not work any other idea, guys? 

Thanks,

kidguayas

---

### Post by Mze on 2008-12-31
Solution by Bruno Rebelo Lobato

solution source: [bug #297836]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/297836")

add this line in your xorg.conf in the section "Device" :

Option "RenderAccel" "0"

This steps solves the problems with Openoffice and Wine apps too.

Then logout and then login

---

### Post by vanadium on 2009-01-01
[quote]It did not work any other idea, guys? [quote]

What did you try and what did not work? Multiple suggestions were given. We can not know what "it" means.

---

### Post by kidguayas on 2009-01-01
Dear Mze;
  Thank you very much. Your suggestion works like a charm. I am posting this last message to lead other ones to the solution.

>>Go to the terminal and type
  >> sudo gedit /etc/X11/xorg.conf
>> Go to 
   Section "Device"
	Identifier	"Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
>> Add this line: Option "RenderAccel" "0"	
I hope this help next person that have a similar problem

---

### Post by dougal04 on 2009-01-03
> **kidguayas said:**
> Dear Mze;
  Thank you very much. Your suggestion works like a charm. I am posting this last message to lead other ones to the solution.

>>Go to the terminal and type
  >> sudo gedit /etc/X11/xorg.conf
>> Go to 
   Section "Device"
	Identifier	"Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
>> Add this line: Option "RenderAccel" "0"	
I hope this help next person that have a similar problem
Thanks. It worked for me too. I had problems with OO.o 2.4 , Opera web browser & K3b.

Ubuntu 8.10 Intrepid
P4 2.66
Nvidia Mx 440 AGP 4x
768Mb Ram

---

