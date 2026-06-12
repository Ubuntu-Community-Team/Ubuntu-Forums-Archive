---
title: "installing GNOME on Kubuntu - how to ?"
date: 2005-10-03
forum: Desktop Environments
---

### Post by JMD on 2005-10-03
hi, I've just made the leap to linux :) I chose ubuntu, but still has to decide between gnome/kde. I read [here]("http://www.kubuntu.org/documentation.php") that > Another concern for users wanting to try Kubuntu, may be that KDE will become their only desktop once it is installed. While we do indeed hope you will choose KDE as your desktop of choice, this is not the case, both destop session types can be run after installing Kubuntu. **Furthermore, during installation you will be given the choice of using either the GNOME Display Manager (GDM) or the K Display Manager (KDM).** So I installed Kubuntu hoping to play with both desktops. Unfortunately, there was no desktop choice during my installation procedure (normal ?). 
Now I wish to install GNOME on my kubuntu distribution, but as a total newbie on linux I don't know how to do do this. It is well documented how to install KDE on Ubuntu, but I couldn't find the reverse. 
Looking in kynaptic, there's many package to select with gnome-*** what do I chose ? 
thanks for the help

---

### Post by heimo on 2005-10-03
There are two metapackages
[LIST]
[*]kubuntu-desktop -> KDE (Kubuntu)   
[*]ubuntu-desktop -> Gnome (Ubuntu) [/LIST] These packages install all the neccessary packages needed for default desktops on Ubuntu/Kubuntu.

---

### Post by tseliot on 2005-10-03
Open Kynaptic and install "ubuntu-desktop"

---

### Post by Knome_fan on 2005-10-03
First off, hi and welcome! :D 

Having no desktop choice during installation is normal. Some people like it, some people don't but as it helps keeping the install to one CD and makes it easier I think it is a good thing.

The easiest way to try out gnome is probably to simply select ubuntu-desktop in kynaptic and install it. That should be all you need to do.

Have fun!

---

### Post by ep0niks on 2005-10-03
The "apt-get install ubuntu-desktop" will download every needed Gnome packages while "apt-get install kubuntu-desktop" gives you every needed KDE packages (if you install the Ubuntu version instead of Kubuntu).

* woops i'm so 1 minute ago

---

### Post by JMD on 2005-10-03
thanks for the quick replies, 
in kynaptik, i did no find the "ubuntu-desktop" package in any section. There is indeed a GNOME Desktop Enviroment section, with about 20 packages, but I don't know which ones to select. 

I will try the command line in #5, sems oh ! so much simpler :) 

thanks again 

PS : "Permission denied in Konsole" How do I input my admin password ?
PPS : in kynaptik, is "gnome-control-center" the right package to install ?

---

### Post by Knome_fan on 2005-10-03
Ah, forgot that, you'll have to enable the online repositories first I think.
Open /etc/apt/sources.list with your favorite editor as root (this should also answer the question about the admin password), for example:
sudo kwrite /etc/apt/source.list

(Note, (K)Ubuntu uses sudo, so to do something as root use sudo programyouwanttorunasroot. To permanently become root in a terminal use sudo -s)

Now enable the online repositories, that is get rid of the # in front of the lines starting with deb and deb-src. Save the file, run apt-get update and ubuntu-desktop should be there.

Have fun!

---

### Post by JMD on 2005-10-03
thank you,

I guess it is an imporant step, however, I seem not to be able to open this file since I get this error :

Error: "/var/tmp/kdecache-jmi" is owned by uid 1000 instead of uid 0"

I'm vey new to linux (2 hours now :) ), therefore I'm completely unable to solve that problem.

---

### Post by Knome_fan on 2005-10-03
Hm, strange.
I just tested it and though I get a similar error kwrite still opens.

Anyway, just use kdesu instead of sudo. This should work (I hope):
kdesu kwrite /etc/apt/sources.list

---

### Post by JMD on 2005-10-03
well, thanks to you I did it :) 
Actually, KWrite opened an empty document named sources.list so I figured it was not working... but I could still open the source.list fle and make the modifications. 
now it is fine. 

Thanks again, these 4 hours on linux taught me at least something :)

PS : About my quote from the first post, people from kubuntu should modify it since it a _false_ statement.

---

### Post by xthaparian on 2005-10-05
Changing Display Manager

Changing between KDM and GDM is made safe and easy with the help of the dpkg-reconfigure. Simply follow the procedure below to change between display managers.

   1. From the Desktop start a shell session or use Kynaptics
   2. Search for gdm, gdm-dekstop, gdm-base, gdm, gnome.
   3. Install all of these.
   4. Now at the prompt enter the following command

   sudo dpkg-reconfigure kdm (If installing GNOME on KDE)
   sudo dpkg-reconfigure gdm ( If installing KDE on Gnome)
                

   3.When prompted enter your password. This will start the Ubuntu Configuration manager. You will remember this screen from the installation, so select OK.
   4.Because there are now two Display Managers installed and only one display manager can be used to manage a given X Server, you will be prompted to select a default. Selected either GDM or KDM then OK.
   5.Shutdown and Restart the computer. When the system boots it will run the display manager of your choice.

---

### Post by urbandryad on 2005-10-05
I might just install KDE. If it works better for me than Gnome, that'll be a relief.

Will I still be able to play majong in KDE? ^__^;

---

### Post by BiggoCharley on 2005-10-06
[QUOTE=heimo]There are two metapackages
[LIST]
[*]kubuntu-desktop -> KDE (Kubuntu)   
[*]ubuntu-desktop -> Gnome (Ubuntu) [/LIST] These packages install all the neccessary packages needed for default desktops on Ubuntu/Kubuntu.[/QUOTE]
Newbie question--Is the vice-versa true also? I have Ubuntu with the Gnome desktop--I like it but I'd like to try KDE also --If I install KDE will I still have access to Gnome or will Gnome be replaced by KDE?

---

### Post by Knome_fan on 2005-10-07
You'll still have access to gnome.

---

### Post by JMD on 2005-10-07
[QUOTE=urbandryad]Will I still be able to play majong in KDE? ^__^;[/QUOTE]

Yes you will, I checked that too :)

---

### Post by xthaparian on 2005-10-07
[QUOTE=BiggoCharley]Newbie question--Is the vice-versa true also? I have Ubuntu with the Gnome desktop--I like it but I'd like to try KDE also --If I install KDE will I still have access to Gnome or will Gnome be replaced by KDE?[/QUOTE]


Yes dude, Actually the KDE is better in the sense that you can have access to both the Gnome and KDE applications in KDE with Fulll Colored Icons associated with them, but its not as good if you install some KDE pakage in Gnome..

So ya you will acess to a lot of applications fomr both the systems.

---

