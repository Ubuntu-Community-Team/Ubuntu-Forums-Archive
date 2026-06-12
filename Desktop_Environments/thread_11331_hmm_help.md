---
title: "hmm help?"
date: 2005-01-16
forum: Desktop Environments
---

### Post by akurashy on 2005-01-16
hello im new to ubuntu but im kinda lost in this forum o.O
anyway i wanted to ask where can i get a nice editor to designs site :)
and is ubuntu compatible to KDE?

---

### Post by Perfect Storm on 2005-01-16
You mean Html editor? Try Nvu

Check here how you install it: [http://ubuntuguide.org/index.html#nvu](http://ubuntuguide.org/index.html#nvu)



.:=The AI Dude=:.

---

### Post by feneks on 2005-01-16
GNOME is the standard GUI but you may use KDE too  :wink: 

But you'll have some homework to do. Open a Shell (also called Terminal)
and type in:
```
sudo gedit /etc/apt/sources.list
```

delete the "#" at the rows
> #deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
save it :wink:

close the terminal/Shell

start Synaptic 
you'll find it at Computer->Systemconfiguration->Synaptic (or similar - my menu is in German)
Click the reload button
search for the paket "kde" and select it
several other pakets are selected automatical
install them

exit GNOME
at the Loginmanager (GDM) click at sessions and choose kde

have a lot of fun ...


--edit--
html editors.
nvu: a WYSIWYG editor 
bluefish: codebased editor of GNOME
quanta plus: codebased editor of KDE - maybe already capable of WYSIWYG
screem: codeased editor (GNOME?)

---

### Post by jakeslife on 2005-01-16
For a web editor, I finally just installed Crossover Office and DW.

---

### Post by akurashy on 2005-01-16
hmm another questoin
how to change resolution?

i have a geforce FX 5200 i know the installer ask what resolution size but this time it didnt ask me and im using 1600 x ??? that it doesnt fit in my monitor :( and the fonts are to little :(
where can i change resolution?

---

### Post by akurashy on 2005-01-16
[QUOTE=feneks]GNOME is the standard GUI but you may use KDE too  :wink: 

But you'll have some homework to do. Open a Shell (also called Terminal)
and type in:
```
sudo gedit /etc/apt/sources.list
```

delete the "#" at the rows

save it :wink:

close the terminal/Shell

start Synaptic 
you'll find it at Computer->Systemconfiguration->Synaptic (or similar - my menu is in German)
Click the reload button
search for the paket "kde" and select it
several other pakets are selected automatical
install them

exit GNOME
at the Loginmanager (GDM) click at sessions and choose kde

have a lot of fun ...


--edit--
html editors.
nvu: a WYSIWYG editor 
bluefish: codebased editor of GNOME
quanta plus: codebased editor of KDE - maybe already capable of WYSIWYG
screem: codeased editor (GNOME?)[/QUOTE]


when i unscommented the text and ran synaptic
it says that it couldnt load  =/

---

### Post by feneks on 2005-01-16
[QUOTE=akurashy]when i unscommented the text and ran synaptic
it says that it couldnt load  =/[/QUOTE]

I hope you just removed the "#" at the two mentioned rows. Otherwise it won't work at all.

When does Synaptic say it can't load? When you want to start Synaptic or when you click the reload button?

---

### Post by akurashy on 2005-01-17
when i start it, it says coudlnt load etc etc
do i need to press reload?

ps. i fixed the resolution

and another question for the people helpng mme :)

i want to divide my HD in 2 partitions 
my hd is of 80 gb, 
fast to the point anyway, if i create a partion in ubuntu how much i have to do?
i wanna divide my windows from linux and how grub going to handle it?

---

### Post by Wim Sturkenboom on 2005-01-17
[QUOTE=akurashy]i have a geforce FX 5200 i know the installer ask what resolution size but this time it didnt ask me and im using 1600 x ??? that it doesnt fit in my monitor :( and the fonts are to little :(
where can i change resolution?[/QUOTE]Edit /etc/X11/XF86Config-4 after creating a backup.
Look for the *screen* section. You will find subsections *display*. In each subsection is a line called *modes* giving all the modes that you can use. It looks like
```
Modes "1600x1200" "1024x768"
```
Remove the 1600x1200 entry.

This way you basically tell X that it can't use 1600x1200 at all.

Another option is using the computer menu on the desktop. Choose system configuration->screen resolution.
Possible disadvantage: this way your login screen will still be in 1600x1200.
Possible advantage: you can still use 1600x1200 if you have to (e.g. graphics design) and other users (if any) still can use higher resolutions.

---

### Post by fng on 2005-01-17
good editors are bluefish and screem (both in universe)

I really like PHPed, but its commercial and a trail can be found at their webby ([http://www.nusphere.com/](http://www.nusphere.com/)).

---

### Post by akurashy on 2005-01-17
thanks all for your support! :D
a real good help :)

---

### Post by akurashy on 2005-01-17
well can anyone help me about the partitions O_o

---

### Post by feneks on 2005-01-17
Does Synaptic work?

if no:
It could be interessting what "etc" means

I prefer to use Synaptic's backend called apt.  To see if you have a problem with Synaptic or with apt I advise you to give apt a try.

```
sudo apt-get update
```
refreshes the list of availiable packages (and  in your case a list of new servers too).
The button "refresh" of Synaptic does the same.

```
sudo apt-get upgrade
```
looks for new versions of already installed packages and installs them.

```
sudo apt-get install kde
```
installs the package of KDE and all additionaly needed packages.

```
apt-cache search catchword
```
helps you to find the packages you need.

---

### Post by feneks on 2005-01-17
[QUOTE=Wim Sturkenboom]Edit /etc/X11/XF86Config-4 after creating a backup.
Look for the *screen* section. You will find subsections *display*. In each subsection is a line called *modes* giving all the modes that you can use. It looks like
```
Modes "1600x1200" "1024x768"
```
Remove the 1600x1200 entry.

This way you basically tell X that it can't use 1600x1200 at all.

Another option is using the computer menu on the desktop. Choose system configuration->screen resolution.
Possible disadvantage: this way your login screen will still be in 1600x1200.
Possible advantage: you can still use 1600x1200 if you have to (e.g. graphics design) and other users (if any) still can use higher resolutions.[/QUOTE]

I read somewhere that  GDM uses the first solution it finds at *modes*. So if you set "1024x768" before "1600x1200" GDM uses "1024x768". Haven't tried it myself but I heaven't read that it didn't worked.

---

### Post by feneks on 2005-01-17
[QUOTE=akurashy]well can anyone help me about the partitions O_o[/QUOTE]

Have a look at 
[http://www.ubuntuforums.org/showthread.php?t=11399](http://www.ubuntuforums.org/showthread.php?t=11399)

---

### Post by akurashy on 2005-01-17
[http://ubuntuforums.org/showthread.php?t=11582](http://ubuntuforums.org/showthread.php?t=11582)

please read that post i really need the help for that! >_<

---

### Post by akurashy on 2005-01-17
im only know for a ftp program
and a good editor that look like dreamweaver at least
my friend told me quanta
but it runs on KDE >_<

---

### Post by feneks on 2005-01-19
[QUOTE=akurashy]im only know for a ftp program
and a good editor that look like dreamweaver at least
my friend told me quanta
but it runs on KDE >_<[/QUOTE]

If you already activated "universe" for Synaptic it's easy to install
```
sudo apt-get install quanta
```
Of course many libraries of KDE will be instaled too. -that's the disadvantage.
But you can use it in GNOME too.

GNOME's standard html-editor is bluefish.

---

### Post by Circle of Owls on 2005-01-19
jEdit is another excellent HTML editor:

[http://www.jedit.org/](http://www.jedit.org/)

It requires Java (Here is the How-to: [http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre) ), which means that you can still use it even when you are stuck with another OS.

---

