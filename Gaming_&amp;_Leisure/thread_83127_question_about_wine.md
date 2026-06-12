---
title: "question about wine"
date: 2005-10-27
forum: Gaming &amp; Leisure
---

### Post by brutaldrummer on 2005-10-27
Is this the correct site to download from? 

[http://www.winehq.com/](http://www.winehq.com/)

also what is the difference between "wine" and "xwine"?

---

### Post by brutaldrummer on 2005-10-28
ok so xwine is a graphical interface for wine. I installed wine and xwine using synaptic, 
Now I don't know how to open xwine. Linux is confusing the hell out of me. I clicked the add applications and it's not in there. So I don't know how to run it.

---

### Post by aysiu on 2005-10-28
Easiest way to do it is through Synaptic or apt-get. To do it through apt-get, just [add extra repositories](http://www.psychocats.net/sources.html), then ```
sudo apt-get update
sudo apt-get install wine
``` To use Wine, just double-click on .exe file, and Wine will automatically *try* to launch the application. It will not work for all .exe files.

Since you're posting this in the gaming section, though, you probably want [Cedega](http://www.transgaming.com/), which is a variant of Wine tailored specifically for gaming.

---

### Post by brutaldrummer on 2005-10-28
o.. well where do i get cedega.

---

### Post by aysiu on 2005-10-28
Underlined words here are usually links.

---

### Post by brutaldrummer on 2005-10-28
I didn't see the underline :D  I do now though. I will click it

---

### Post by brutaldrummer on 2005-10-28
so do is there a cedega that I don't have to pay for?

---

### Post by aysiu on 2005-10-28
[QUOTE=brutaldrummer]so do is there a cedega that I don't have to pay for?[/QUOTE] Can I ask why you want to use Linux (or Ubuntu specifically)? I'm not trying to scare you away, but a lot of Linux users dual-boot because of games. Cedega may help you play most games, but you do have to pay for it. There are ways around it, but you have to compile Winex yourself (Google will help you with this). If that seems too much trouble, why not just use Windows.

Linux is not ideal for serious gamers.

---

### Post by schizoid_embolism on 2005-10-28
[QUOTE=aysiu]To use Wine, just double-click on .exe file, and Wine will automatically *try* to launch the application. It will not work for all .exe files.[/QUOTE]

I have a question.  What if that .exe file is an installation file?  Will it try to install the program in my Linux file system, if that is even possible?

Jeremy

---

### Post by ofek on 2005-10-28
well wine kinda making apps for windows "think" u are using windows.
most installers should work and install ur program.
 they will probably install it to something like /home/.wine/c/program files/ but im not sure. 
i remember i installed internet explorer in a linux system because i didn't like mozilla that much at that time and even installed gta2 and played over my wireless network with a friend. u can try it yourself and just see if it works for u.

---

### Post by aysiu on 2005-10-28
[QUOTE=ofek]well wine kinda making apps for windows "think" u are using windows.
most installers should work and install ur program.
 they will probably install it to something like /home/.wine/c/program files/ but im not sure.[/QUOTE] I just installed Filezilla yesterday using Wine, and it asked me where I wanted to install it, and I could select my /home directory in Ubuntu.

---

### Post by wishyjr on 2005-10-28
well, in theory if you could mount the partition with windows on, couldnt you just run the .exe files straight from there?

---

### Post by aysiu on 2005-10-28
[QUOTE=wishyjr]well, in theory if you could mount the partition with windows on, couldnt you just run the .exe files straight from there?[/QUOTE] It depends. Sometimes the relative .dll paths aren't right. Sometimes it's trying to draw on a profile that doesn't exist because you're running it from somewhere that doesn't have a Windows profile. I also found, for example, when running Filezilla from the Windows partition that it wouldn't rightly transfer files from Ubuntu to the server. When I ran it from the Filezilla I installed with Wine, it worked fine, though.

---

### Post by KLineD on 2005-10-28
[QUOTE=aysiu]I just installed Filezilla yesterday using Wine, and it asked me where I wanted to install it, and I could select my /home directory in Ubuntu.[/QUOTE]

It's better to install it to wine's drive_c In your home directory you should have a hidded directory (with a dot preceeding its name) called .wine 

Inside drive_c (or something similar) should be a directory structure resembling a windows installation with the usual windows, program files, etc. You can then navigate to you program exe file and launch it by double clicking.

One thing I like about Kubuntu is that it places programs installed with wine directly in the menu. I don't know if there's something similar for gnome but it would be great so I get the menu entry and the app icon automatically and not have to extract the icon and make a link to the app with smeg.

---

### Post by xequence on 2005-10-28
I know in cedega there it makes a "Transgaming_Drive" in my home folder, where it stores all things. Its like a virtual C: drive. When you install things, lets say it would install to "C:/Program Files/UnrealTournament" would now probably go to "/home/insertnamehere/Transgaming_Drive/Program Files/Unreal Tournament".

I do know when I run Photofiltre (art program) in cedega, I can choose to save my file to anywhere in my linux system.

---

### Post by aysiu on 2005-10-28
[QUOTE=KLineD]It's better to install it to wine's drive_c In your home directory you should have a hidded directory (with a dot preceeding its name) called .wine 

Inside drive_c (or something similar) should be a directory structure resembling a windows installation with the usual windows, program files, etc. You can then navigate to you program exe file and launch it by double clicking.[/QUOTE] Wow! I didn't know that! Thanks for the tip.

---

