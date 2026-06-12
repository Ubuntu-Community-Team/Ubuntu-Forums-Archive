---
title: "Create a Unity Launcher"
date: 2011-05-10
forum: Desktop Environments
---

### Post by josian_220 on 2011-05-10
Hello I was wondering if anyone out there could help find (at least a easy way :P) to create a launcher for a application called Lince (it is some kind of spell corrector Portuguese). To download it just go here:

[http://www.portaldalinguaportuguesa.org/?action=lince](http://www.portaldalinguaportuguesa.org/?action=lince)

This is a java application to install it I ran it like a normal .jar file

```
sudo java -jar /location/Lince-instalador.jar
```and then it installs by default to /usr/local/Lince. There is another file called Lince.jar which can be made executable and easily run but when doing so using unity there is a issue... I created a .desktop file for it as shown bellow:

[Desktop Entry]
Version=1.0
Terminal=false
Icon=/usr/local/Lince/icone_lince_32.png
Type=Application
Categories=Office;
Exec=Lince
TryExec=Lince
Name=Lince (1.2.12)
X-MultipleArgs=false
StartupNotify=true

But when I run it appears another icon instead of just displaying it is a running application in the same launcher (as shown in the image bellow). If anyone knows a solution I would be really grateful if you could share it :P

P.S - I forgot to mention, I made a symbolic link of the /usr/local/Lince.jar to /usr/bin and I called it just Lince, that's why in the launcher I just wrote Lince to execute it.

---

### Post by mc4man on 2011-05-10
That is similar to what can happen with some wine progs - an icon to launch the prog only launches it, then another icon controlling opens (Wine icon

I've fixed that here but never tried a java app - do you have a link to 'lince'?
side note - /usr/local/bin should be in your path and normally no reason to create a link in /usr/bin

---

### Post by josian_220 on 2011-05-10
Unfortunately it does not create that link in the symbolic link that's why I created one, but answering your question the link is in the website I gave above, just go there and press in the Tux (the penguin) icon and you can download the application there. Could you please tell me how did you managed to do that with the wine applications?

---

### Post by josian_220 on 2011-05-10
This seems to be the same problem happening with Minecraft.

---

### Post by mc4man on 2011-05-10
This isn't the same as wine (where a Wine Window Program Loader icon appears

See 2 things here - the launcher opens a smaller rectangular window, then lince opens with a new lince icon. The controlling icon can then only close lince, not open

The best solution here to not waste icon space was to add lince as a quicklist entry (used to open), then close with the icon that appears which will then disappear when you exit lince

So here used my Utility launcher menu to add lince, though maybe if you have several java apps then create a 'java apps' icon where the quicklists menu launches them

Basically what's shown here - create a basic .desktop, I leave the Exec= empty, then add what ever you wish to be available in the quicklist
[http://ubuntuforums.org/showthread.php?p=10778758#post10778758](http://ubuntuforums.org/showthread.php?p=10778758#post10778758)

The quicklist entry I used for lince (not symlinked, left as installed, though I did make Lince.jar executable
```

[Lince Shortcut Group]
Name=Lince
Exec=java -jar /usr/local/Lince/Lince.jar
TargetEnvironment=Unity

```

---

### Post by josian_220 on 2011-05-11
So there's no apparent solution :( that's a shame well I'll stick with a launcher list within LibreOffice then.

---

### Post by mc4man on 2011-05-11
> **josian_220 said:**
> So there's no apparent solution :( that's a shame well I'll stick with a launcher list within LibreOffice then.
doesn't seem to be (as far as a single standalone launcher

Just to mention - it turns out Lince does create a .desktop - though because of how installed ends up in /root/.local/share/applications
here it is - 
```
[Desktop Entry]
Categories=
Comment=Clique aqui para iniciar a aplicação Lince
Comment[en]=Clique aqui para iniciar a aplicação Lince
Encoding=UTF-8
Exec=java -Xmx1024m -jar "/usr/local/Lince/Lince.jar"
GenericName=
GenericName[en]=
Icon=/usr/local/Lince/icone_lince_32.png
MimeType=
Name=Lince
Name[en]=Lince
Path=/usr/local/Lince
ServiceTypes=
SwallowExec=
SwallowTitle=
Terminal=false
TerminalOptions=
Type=Application
URL=
X-KDE-SubstituteUID=false
X-KDE-Username=root

# created by com.izforge.izpack.util.os.Unix_Shortcut $Revision: 2910 $
# $Id: Unix_Shortcut.java 2910 2009-12-14 08:29:35Z jponge $

```

---

