---
title: "LibreOffice Writer mistake?"
date: 2013-05-02
forum: Desktop Environments
---

### Post by madnbri on 2013-05-02
Hi,
I've got:
xubuntu 12.10 (waiting a bit before upgrading)
+ LibreOffice Writer 3.6.2.2 (from package list)
now...
But I had this at earlier versions of system and Writer and...
never worked correct at me.
Contets of current page disappear during typing. Is this completely useless or **I** forgot something to do (this second is the reason, I think)?
Thanks in advance:
m

---

### Post by Resistent on 2013-05-02
I am sometimes using LibreOffice Writer, but it never happened that the whole content disappeared (not in MS Office, not LibreOffice, not OpenOffice, not AbiWord).
--> I think it was your fault, somehow you selected all text. (and you did that very fast, you could not realize that everything is marked, or you did not look at the monitor).

On my Netbook, happens often, the cursor moves away so I am writing on the wrong position in the text. It's because the touchpad is very sensible.

---

### Post by madnbri on 2013-05-02
> **Resistent said:**
> I am sometimes using LibreOffice Writer, but it never happened that the whole content disappeared (not in MS Office, not LibreOffice, not OpenOffice, not AbiWord).
--> I think it was your fault, somehow you selected all text. (and you did that very fast, you could not realize that everything is marked, or you did not look at the monitor).

On my Netbook, happens often, the cursor moves away so I am writing on the wrong position in the text. It's because the touchpad is very sensible.

No. When I type, the text disappears partially or completely. This happens at scroll also.
That's why LibreOffice Writer is useless at me.
Any other idea?

---

### Post by Resistent on 2013-05-02
> **madnbri said:**
> No. When I type, the text disappears partially or completely. This happens at scroll also.
That's why LibreOffice Writer is useless at me.
Any other idea?

I think this is a visualisation problem. A bug.

And what happens when you only scroll down and than save the file, than reopen it. Can you see the whole text again ?

Did you already a restart of your system? Bugs only occur again, if you make the same steps as before, but you never know
which and how many steps lead to this problem, after restart and again trying the Writer, the chance is high that you
don't make the same step-chain again. So this why I think after restart it will not occur again.

---

### Post by madnbri on 2013-05-02
> **Resistent said:**
> I think this is a visualisation problem. A bug.

And what happens when you only scroll down and than save the file, than reopen it. Can you see the whole text again ?

Did you already a restart of your system? Bugs only occur again, if you make the same steps as before, but you never know
which and how many steps lead to this problem, after restart and again trying the Writer, the chance is high that you
don't make the same step-chain again. So this why I think after restart it will not occur again.

Text is invisible only at scrolling. Save - restart Writer/sys: everything is ok still I do not type or scroll. This is returning problem any way.

---

### Post by Resistent on 2013-05-03
> **madnbri said:**
> Text is invisible only at scrolling. Save - restart Writer/sys: everything is ok still I do not type or scroll. This is returning problem any way.

I meant restarting the whole Linux..

1. Can you try another "Desktop Enviroment" at login?

2. Did you make an update already?

```
sudo apt-get install update
sudo apt-get install upgrade
```

---

### Post by madnbri on 2013-05-03
> **Resistent said:**
> I meant restarting the whole Linux..

1. Can you try another "Desktop Enviroment" at login?

2. Did you make an update already?

```
sudo apt-get install update
sudo apt-get install upgrade
```

1. No, I can't/I won't. XFCE was the best I found at Ubuntu, still Gnome had been gone.
2. Yes, I did many.

---

### Post by Resistent on 2013-05-03
> **madnbri said:**
> 1. No, I can't/I won't. XFCE was the best I found at Ubuntu, still Gnome had been gone.
2. Yes, I did many.

There is a new LibreOffice Version 4.2 !
Even you added the repository to be able to update LibreOffice, with "upgrade" you cannot catch it.

Here is how I solved to update (exaclty now), my LibreOffice 3.6.6.2 to   Version 4.0.2.2 (Build ID: 400m0(Build:2)
Very important: use "**[COLOR=#ff0000]dist[/COLOR]**-upgrade" instead of "upgrade".

> [COLOR=#000000][FONT=Courier New]sudo add-apt-repository ppa:libreoffice/[/FONT][/COLOR][COLOR=#000000][FONT=Courier New]ppa[/FONT][/COLOR][COLOR=#000000][FONT=Courier New]
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu][FONT=Courier New]sudo apt-get update[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]sudo apt-get [/FONT][/COLOR][COLOR=#ff0000][FONT=Courier New]**dist**[/FONT][/COLOR][COLOR=#000000][FONT=Courier New]-upgrade[/FONT][/COLOR]

Looks like, for Ubuntu, a new Version of LibreOffice is not an update. It's a "new application"...

maybe you also read this: [http://askubuntu.com/questions/252612/how-do-i-install-libreoffice-4](http://askubuntu.com/questions/252612/how-do-i-install-libreoffice-4)

---

### Post by Buntu Bunny on 2013-05-03
Madnbri, you didn't accidentally hit the insert key so that the text is being overwritten?

Resistent, I didn't know about the new version. I've been using LO a lot lately, so I'll have to look into this. Thanks

---

### Post by madnbri on 2013-05-04
> **Resistent said:**
> There is a new LibreOffice Version 4.2 !
Even you added the repository to be able to update LibreOffice, with "upgrade" you cannot catch it.

Here is how I solved to update (exaclty now), my LibreOffice 3.6.6.2 to   Version 4.0.2.2 (Build ID: 400m0(Build:2)
Very important: use "**[COLOR=#ff0000]dist[/COLOR]**-upgrade" instead of "upgrade".



Looks like, for Ubuntu, a new Version of LibreOffice is not an update. It's a "new application"...

maybe you also read this: [http://askubuntu.com/questions/252612/how-do-i-install-libreoffice-4](http://askubuntu.com/questions/252612/how-do-i-install-libreoffice-4)

OK. This is solved, but I have to share a thing:
```
$ sudo apt-get update
$ sudo apt-get dist-upgrade
```
**doesn't** work. I don't know the reason, but I had to look for another way:
```
$ sudo update-manager -d
```
This is the X supported version of distribution upgrade, and this is the working way.

---

### Post by Resistent on 2013-05-06
you also have to to first:

[COLOR=#000000][I][FONT=Courier New][COLOR=#ff0000]sudo add-apt-repository ppa:libreoffice/ppa[/COLOR]

and then

[/FONT][/I][/COLOR][COLOR=#ff0000]sudo apt-get update[/COLOR]
[COLOR=#000000][COLOR=#000000][I][FONT=Courier New]
and then

[/FONT][/I][/COLOR][/COLOR][COLOR=#ff0000]sudo apt-get dist-upgrade[/COLOR][COLOR=#000000][COLOR=#000000][I][FONT=Courier New]

[/FONT][/I][/COLOR][/COLOR][COLOR=#000000][COLOR=#000000][I][FONT=Courier New]

You did it like this ??[/FONT][/I][/COLOR][/COLOR]

---

### Post by madnbri on 2013-05-08
> **Resistent said:**
> you also have to to first:

[COLOR=#000000][I][FONT=Courier New][COLOR=#ff0000]sudo add-apt-repository ppa:libreoffice/ppa[/COLOR]

and then

[/FONT][/I][/COLOR][COLOR=#ff0000]sudo apt-get update[/COLOR]
[COLOR=#000000][COLOR=#000000][I][FONT=Courier New]
and then

[/FONT][/I][/COLOR][/COLOR][COLOR=#ff0000]sudo apt-get dist-upgrade[/COLOR][COLOR=#000000][COLOR=#000000][I][FONT=Courier New]

[/FONT][/I][/COLOR][/COLOR][COLOR=#000000][COLOR=#000000][I][FONT=Courier New]

You did it like this ??[/FONT][/I][/COLOR][/COLOR]

Yes, but didn't work. I couldn't observe which repositories was deleted by aptitude, maybe this one also.

And oh yes... That happened I always experience in Ubuntu at distro upgrade:
It is slow, doesn't work correctly and is all the lousy. I usually delete Ubi and choose another linux after googling.
...and googling now...

---

