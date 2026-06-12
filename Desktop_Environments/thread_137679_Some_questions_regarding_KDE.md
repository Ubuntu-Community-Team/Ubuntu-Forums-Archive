---
title: "Some questions regarding KDE"
date: 2006-02-28
forum: Desktop Environments
---

### Post by Mis_Uszatek on 2006-02-28
Hello everyone

1) I have been using for a while Gnome, now I'm using KDE, but I'm still using some applications from Gnome. The problem is, that the fonts are very, very small. I would like to make them bigger but I don't know where and how.

2) I would like to set some defaults, like webbrowser for example. When I clik on link in mail in Kontact, Konqueror starts, but I would like Opera instead Konqueror. Where I can change this?

3) When I type 'java -version' in terminal, version which I'm using is 1.4.2. I have installed(for Eclipse) Sun Java 1.5 in different directory, but I don't know how to set in system, that it should be using Sun1.5 instead 1.4.2.

4) Are there in KDE some other task/system manager than 'KDE SysGuard' or 'Ssytem Monitor'? Both of them are too big, and I would like to have them on the panel, or somewhere in background.

Thanks to everyone who will be helpful.

---

### Post by gingermark on 2006-02-28
[QUOTE=Mis_Uszatek]1) I have been using for a while Gnome, now I'm using KDE, but I'm still using some applications from Gnome. The problem is, that the fonts are very, very small. I would like to make them bigger but I don't know where and how.[/quote]
System Settings-->Appearence-->GTK Styles and fonts.

[QUOTE=Mis_Uszatek]2) I would like to set some defaults, like webbrowser for example. When I clik on link in mail in Kontact, Konqueror starts, but I would like Opera instead Konqueror. Where I can change this?[/quote]
System Settings-->User Account-->Default Applications.

You can also set file associations, but I can't find that section in Kubuntu's System Settings. But in KControl (the default KDE Control Centre) they are in the KDE Components section. (Just run the command 'kcontrol')

[QUOTE=Mis_Uszatek]4) Are there in KDE some other task/system manager than 'KDE SysGuard' or 'Ssytem Monitor'? Both of them are too big, and I would like to have them on the panel, or somewhere in background.[/quote]
Sort of. Right click on the panel, and select "Add Applet to Panel".
There are several applets that should meet your requirements.

There are also several SuperKaramba themes that do this nicely. I recommend the 'Aero All In One' theme. Once SuperKaramba is installed you can download themes from [www.kde-look.org](www.kde-look.org)

Not too sure on the proper answer for the Java question, sorry.

---

### Post by Ptero-4 on 2006-02-28
> 
Quote:
Originally Posted by Mis_Uszatek
1) I have been using for a while Gnome, now I'm using KDE, but I'm still using some applications from Gnome. The problem is, that the fonts are very, very small. I would like to make them bigger but I don't know where and how.
System Settings-->Appearence-->GTK Styles and fonts.

Hi gingermark. I think that the OP was asking how to change the KDE fonts, not the GTK ones. The KDE fonts are in Kcontrol-->Look and Feel-->Fonts.

---

### Post by Mis_Uszatek on 2006-02-28
> Hi gingermark. I think that the OP was asking how to change the KDE fonts, not the GTK ones. The KDE fonts are in Kcontrol-->Look and Feel-->Fonts.

No, the question was regarding GTK. I wanted to change Gnome application fonts in KDE, and 
> System Settings-->Appearence-->GTK Styles and fonts.
is correct.

I have find out how to set java for opera also
Tools->Preferences->Advanced->Contents->Java options
and there you have to set correct path.

Thanks also for info about System Managers.

But I have the question about default application.

I have done as you have said, 
System settings->User acounts->default application
and now, when I click on the link in Kontakt, opera starts. Ok.
But the behaviour is very strange.
1)Appears downloading windows, the content of the html page is downloading on the disc
2)then opera appears, and tries to open file from disc

The behaviour with the Firefox is the same.

Aby ideas?

Thanks by the way for other answers.

---

### Post by gingermark on 2006-02-28
I'm afraid I don't use Kontact, but I'll give this a go.

Press Alt+F2 and type 'kcontrol'. Press enter. This will bring up Kcontrol, which seems to have more options than System Settings. Click on KDE Components, followed by File Associations. Find the file format you want, click on the embedding tab, and select "show file in separate viewer".

I think that should do it, but don't be surprised if it doesn't. I could well be wrong on that one.

---

### Post by Jucato on 2006-02-28
For the java problem, try this:
```
 sudo update-alternatives --config java
```
and choose the java version that you want the system to recognize as default.

About Firefox/Opera browser, does this behavior happen always? I think it only happens on some contents. But I don't think it should be the default behavior.

(System Settings doesn't have the File Association option. Another reason why I hate it and prefer to use KControl :D)

---

### Post by Mis_Uszatek on 2006-03-01
> About Firefox/Opera browser, does this behavior happen always? I think it only happens on some contents. But I don't think it should be the default behavior.

Yes, it is always happening :(
But I have fixed it a moment ago :DDD

Standard command was Opera, but for example for Konqueror was
kfmclient openURL %u text/html
I have changed Opera -> Opera %u and now it is working ;-)

As for the > For the java problem, try this:

Code:

 sudo update-alternatives --config java
and choose the java version that you want the system to recognize as default.
I had only two paths, but both were incorrect

I had added one path
```

sudo update-alternatives --install /etc/alternatives/java java /usr/jdk1.5.0/jdk1.5.0_06/jre/bin/java 1

```

and then set proper, but now when I type
```
~/java --version
```
it is not working.

I have changed to the previous one, and it is still not working :(

---

