---
title: "kde control (adminstration mode)"
date: 2005-04-21
forum: Desktop Environments
---

### Post by adrislayer on 2005-04-21
Well, hi everyone since it's my first post.

Here is my problem: I'm quit a newbie in linux so I must rely often to graphical application to modify my settings and kde control suits me the best...

But here comes the problem: When I go in network settings, I must operate in root to change everything so I click in adminstative mode then I enter my root password that I have introduce with "sudo passwd root" ... but then, nothing happend. And so I cannot change anything and I'm unable to connect to internet.

So I like to know how I'm able to enable the root fonction to enter in kde control adminstrative mode. I've figured out that in ubuntu the classic root is disable or something like that but I don't know how to change that...

If you can tell me how, U have already all my thanks.

And not to post another thread:

Wich application must I install to change "powerspace", "userspace", etc with the ACPI? I havn't seen anything like that in kubuntu. Of course it will be loved if it where a kde application or something like that.

I'm working in an Acer Aspire 1680 so the acpi cannot inicate the battery but the cpu throwling is enable. (that isn't any of kubuntu problem it's just that acpi doesn't work fine with acer already). But it may be of use for U to know.

Well, I hope you will understand everything cause I'm quit bad when I must write in english...

---

### Post by Sham on 2005-04-21
When you click on network settings you need to input your user password, NOT your root password. I made this mistake aswell ;-)

---

### Post by adrislayer on 2005-04-21
thanks

but the problem may be the same because both my root password and user password are the same.

I know it isn't very secure but ...

So, I will try changing my user password to have a different one from the root and try again.

---

### Post by adrislayer on 2005-04-21
no it doesn't work...

I'll try to explain exactly what happend: 
When I click on adminstrative mode I have a window that appear to prompt my password. I do so and then after a few seconds it refresh the network page but not in adminstrative mode...

I like kde lot's more but if that doesn't work, i think i will stay with gnome and install ubuntu again.

---

### Post by Sham on 2005-04-21
[QUOTE=adrislayer]no it doesn't work...

I'll try to explain exactly what happend: 
When I click on adminstrative mode I have a window that appear to prompt my password. I do so and then after a few seconds it refresh the network page but not in adminstrative mode...

I like kde lot's more but if that doesn't work, i think i will stay with gnome and install ubuntu again.[/QUOTE]


Hmm, thats strange. When I click on networking, the fist thing it asks for is my password. When I give it, it then goes into the networking dialogue box. There is no button for administrator mode. I'm a little confused about this  :???: 

I hope we are looking at the same thing!

---

### Post by adrislayer on 2005-04-21
I will post a screen so that's everything will be clear...

---

### Post by Sham on 2005-04-21
[QUOTE=adrislayer]I will post a screen so that's everything will be clear...[/QUOTE]


I think I know what you mean. You go into the control centre first, and then hit the admin mode button? I just tried this, and my user password works.

---

### Post by adrislayer on 2005-04-21
well here we go:
the page I have to log in adminstrative mode:
[http://membres.lycos.fr/adrislayer/screen3.png](http://membres.lycos.fr/adrislayer/screen3.png)

when I must enter my userpassword
[http://membres.lycos.fr/adrislayer/screen1.png](http://membres.lycos.fr/adrislayer/screen1.png)

And the page I'm redirected right after that. And when I click again on network it's just the same as screen3...
[http://membres.lycos.fr/adrislayer/screen2.png](http://membres.lycos.fr/adrislayer/screen2.png)

---

### Post by Sham on 2005-04-21
[QUOTE=adrislayer]well here we go:
the page I have to log in adminstrative mode:
[http://membres.lycos.fr/adrislayer/screen3.png](http://membres.lycos.fr/adrislayer/screen3.png)

when I must enter my userpassword
[http://membres.lycos.fr/adrislayer/screen1.png](http://membres.lycos.fr/adrislayer/screen1.png)

And the page I'm redirected right after that. And when I click again on network it's just the same as screen3...
[http://membres.lycos.fr/adrislayer/screen2.png](http://membres.lycos.fr/adrislayer/screen2.png)[/QUOTE]


Mine does the same thing. When I enter my password the screen remains the same, but this time when I click on eth0 the configure button lights up signalling that I can now use it. Did you try configuring the network after you enetered the password, or did you assume that it hadn't worked because the buttons were still blanked out?

---

### Post by segrewb on 2005-04-21
Check out this [thread](http://www.ubuntuforums.org/showthread.php?t=26444&highlight=administration+mode) for a solution.  Worked for me.

Segrewb

---

