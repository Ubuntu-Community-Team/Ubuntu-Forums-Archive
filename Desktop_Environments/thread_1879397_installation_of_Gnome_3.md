---
title: "installation of Gnome 3"
date: 2011-11-11
forum: Desktop Environments
---

### Post by alain.roger on 2011-11-11
Hi,

i have some issue while installing Gnome 3 on ubuntu 11.10.
i tried to follow steps from [https://debianhelp.wordpress.com/2011/10/07/how-to-install-gnome-3-desktop-environment-in-ubuntu-11-10/](https://debianhelp.wordpress.com/2011/10/07/how-to-install-gnome-3-desktop-environment-in-ubuntu-11-10/) however i got some error message.

first steps run well:
```
sudo add-apt-repository ppa:ricotz/testing sudo apt-get update
```

Problem started later with:
```
sudo apt-get install gnome-tweak-tool gnome-shell-extensions-user-theme
```

it returns me:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-shell-extensions-user-theme is already the newest version.
gnome-tweak-tool is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gnome-shell : Depends: libglib2.0-0 (>= 2.31.0) but 2.30.0-0ubuntu4 is to be installed
 libglib2.0-0 : Breaks: libglib2.0-0:i386 (!= 2.30.0-0ubuntu4) but 2.31.0+git20111109.759c0e93-0ubuntu1~11.10~ricotz0 is to be installed
 libglib2.0-0:i386 : Breaks: libglib2.0-0 (!= 2.31.0+git20111109.759c0e93-0ubuntu1~11.10~ricotz0) but 2.30.0-0ubuntu4 is to be installed
 libglib2.0-bin : Depends: libglib2.0-0 (= 2.31.0+git20111109.759c0e93-0ubuntu1~11.10~ricotz0) but 2.30.0-0ubuntu4 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

so if i understood well my version of libraries is higher than the requested.
have you already had such situation ?

thx

---

### Post by magneze on 2011-11-11
On 11.10 it's much simpler - you don't need ricotz testing, remove that. Just install gnome-shell.

sudo apt-get install gnome-shell

and you're done. Select GNOME from the login screen.

---

### Post by alain.roger on 2011-11-11
thank a lot, it works... really ubuntu is far better than Windows and Fedora :-) i love it!

---

### Post by 3Miro on 2011-11-11
There is some confusion about Gnome and Ubuntu. Ubuntu 11.10 comes by default with Gnome 3 and Unity interface. Unity is just compiz windows manager and custom UI. The default windows manager and interface for Gnome 3 is Gnome-shell. In order to get Gnome-shell for 11.10, all you need to do is install it from the software center:
```
sudo apt-get install gnome-shell
```

---

### Post by alain.roger on 2011-11-11
> **3Miro said:**
> There is some confusion about Gnome and Ubuntu. Ubuntu 11.10 comes by default with Gnome 3 and Unity interface. Unity is just compiz windows manager and custom UI. The default windows manager and interface for Gnome 3 is Gnome-shell. In order to get Gnome-shell for 11.10, all you need to do is install it from the software center:
```
sudo apt-get install gnome-shell
```

I don't know about that you are talking using word "confusion" for my Gnome is an interface for linux and has nothing to do with Windows. if by confusion you are talking about my previous sentence i just wanted to tell that Ubuntu as OS is far better than Windows and basic interface of ubuntu 11.10 is better than last Fedora interface i used... nothing more :-)

By the way after all updates i face another issue with Gnome 3 "Advanced settings".
when i click on "Theme" the Shell theme is disable and i have an orange triangle about 
"could not list shell extensions"

using google i found following links:
[http://it-diary.com/linux/install-gnome-shell-themes-ubuntu-11-10/](http://it-diary.com/linux/install-gnome-shell-themes-ubuntu-11-10/)
[http://www.omgubuntu.co.uk/2011/10/how-to-install-gnome-shell-themes-in-ubuntu-11-10/](http://www.omgubuntu.co.uk/2011/10/how-to-install-gnome-shell-themes-in-ubuntu-11-10/)
but they didn't solve my problem.

any idea where is the problem located ?\thx.
A.

---

### Post by 3Miro on 2011-11-11
> **alain.roger said:**
> I don't know about that you are talking using word "confusion" for my Gnome is an interface for linux and has nothing to do with Windows. if by confusion you are talking about my previous sentence i just wanted to tell that Ubuntu as OS is far better than Windows and basic interface of ubuntu 11.10 is better than last Fedora interface i used... nothing more :-)


Windows Manager is the top most part of any Linux desktop environment and has nothing to do with the Windows operating system created by Microsoft Corporation. Traditional desktop environments like KDE, XFCE, LXDE and Gnome 2 come with more or less similar interface (i.e. panels, applets and menus). The new Gnome 3 (by default) comes with its own Windows Manager (based on Mutter) and its own new user interface. The new combination of WM and UI is called Gnome-shell.

Canonical (the company behind Ubuntu), has decided that they don't want to use Gnome-shell, instead they created Unity. Unity is a plugin for the compiz Windows Manager that creates a new interface. Thus Ubuntu now comes with Gnome 3 and the Unity UI (which includes compiz WM).

The confusion comes from several places. Specifically in the instructions that you were reading, they referred to Ubuntu 11.04 which came with Gnome 2 and Unity, hence in 11.04 you have to take some extra steps to install Gnome 3. In Ubuntu 11.10 you no longer have to worry about that, if you want all of Gnome 3 then all you have to do is install Gnome-shell.

Another source of confusion is that people don't distinguish between Gnome 3 (which is installed by default in 11.10) and Gnome-shell (which isn't installed) and somehow people think that Ubuntu is abandoning Gnome altogether (although there is general disagreement between Canonical and the Gnome developers).

---

### Post by alain.roger on 2011-11-12
I was only talking about OS, but anyway thank a lot for those information :-)
Can you tell me how to "activate" shell theme ? i didn't find information on internet.

---

### Post by Frogs Hair on 2011-11-12
When you login after the user name is selected  use the tool icon on the login screen to select the session before entering the password .

---

### Post by alain.roger on 2011-11-12
This i know this is the gear icon.
i meant by sheel theme in the Gnome menu Applications > Other > 3 Advanced Settings > Theme > Shell extension. :-)

---

### Post by magneze on 2011-11-15
> **alain.roger said:**
> thank a lot, it works... really ubuntu is far better than Windows and Fedora :-) i love it!
Gnome 3 is fantastic. I use it everyday for work.

---

