---
title: "installing ndiswrapper"
date: 2006-06-10
forum: Desktop Environments
---

### Post by moncsco on 2006-06-10
Can anyone tell me how to install ndiswrapper?:confused:  the instruction on the wiki site is driving me crazy](*,) . this is my first linux installation and i have found out that i should install ndiswrapper for my wireless card (netgear wg311v3) to work using windows drivers. can anyone please help me?

---

### Post by deathbyswiftwind on 2006-06-10
Id be glad to help. Are you trying to install ndiswrapper from the repos or do you want to compile from source? Either way its pretty easy.

----The Repo Way----
1. Open up synaptic via menus system>administration>synaptic package manager
2. Go to settings>repositories
3. Click on each listing and edit it to include multiverse,universe, and non-free
4. Close repo list and hit the reload button in synaptic
5. Search ndiswrapper (3 items should appear)
6. Select ndiswrapper-utils and you may want to select ndisgtk(gui for installing drivers)
7.With ndisgtk simple go to where your drivers are installed and select the inf file
                                                     or
Copy your drivers onto your desktop. Open a terminal and enter the following command

sudo ndiswrapper -i ~/Desktop/****.inf (replace the **** witht he driver name)

With either method you will still have to enter the following two commands into your terminal

sudo modprobe ndiswrapper

sudo ndiswrapper -m

Configure your network via the menus  System>Administration>Networking

After all of this youll be done. I would recommend a shutdown at this point. If you just restart your wireless lights wont shut off. Shutdown and then turn your pc back and on see if everything is working

This is the method I recommend you could do the source but Im not very good at debugging build error messages so youll have to ask for help.

---

### Post by az on 2006-06-10
Great, but if you cannot get onto the net, you already have it on your cd.

If you installed from the desktop cd, boot into ubuntu and then inster the cd.

You will get prompted about some packages on the cd.  Add them to your list of repos, as the dialogue suggests and then search for ndiswrapper-utils using the package manager and install it.

That's it.


If you installed using the alternate cd, the packages are already added to your list so just install ndiswrapper-utils using synaptic.

---

### Post by moncsco on 2006-06-12
Thanks for the help. I have managed to install ndiswrapper. Unfortunately the device doesnt show up in the networking window. But ndiswrapper says driver present hardware present and it is also present in the device manager. Any help?

---

### Post by billw11 on 2007-08-10
this is bothering me. how come i followed those instructions exactly , yet ndiswrapper isnt an option to install?
bad cd?

---

### Post by billw11 on 2007-08-11
its ok thanks for all the help guys.
i gave up last night on ubuntu. ndiswrapper is nowhere to be found on the install cd. i finally checked to see cd for errors , none found.
i dont need internet connection at all times, but when i cant even install anything on ubuntu without downloading files, well , cant go anywhere.
theres no such thing as an O/S that has everything installed unless you only want to play card games.

i just dont have the patience to keep switching back n forth to windows to get an internet connection, so drive is now formatted to ntfs. 80 gig is too small for anything much useful for me , so ill use it as a temp folder for windows.

im not comfortable with workarounds and believe that if hardware is installed , it should be recognized and used

---

### Post by Serial211 on 2007-10-01
I could not find the Ndiswrapper either on the CD. however when i plugged in my wired network card and did the search again it came right up. i think it pulls the files from the internet.

---

### Post by FoxOne on 2007-12-21
> **billw11 said:**
> 
im not comfortable with workarounds and believe that if hardware is installed , it should be recognized and used

1. If your not comfortable with work arounds I guess you must take issue with Service Pack and two for windows. (Guess what, they're work arounds... they all stem from a hotfix in some way)

2. I totally agree, if the hardware is installed, it should just work. No, write to your hardware manufactures and ask them to start releasing open source drivers. The reason Linux has so many work arounds (ie ndiswrapper) is because we live in an society that is obsessed with Windows bcause they're not aware they have **choice**. And because of that, hardware manufactures tailor drivers and software for that platform. Same issue, to a much lesser degree, for OSX users. Of which I once was.

---

### Post by khughitt on 2007-12-21
Anyone know a way to find the drivers for a card card that uses an install wizard to install the drivers? I'm trying to setup ndswrapper for a [Netgear WPN311]("http://kbserver.netgear.com/release_notes/d103109.asp"), but the only install option they provide for the drivers is a windows install-wizard. I even tried setting installing the drivers on a separate windows machine and then looking for the .inf files, but have not had any luck... 

Any suggestions?

---

