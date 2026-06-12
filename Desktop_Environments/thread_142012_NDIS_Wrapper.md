---
title: "NDIS Wrapper"
date: 2006-03-09
forum: Desktop Environments
---

### Post by Geffers on 2006-03-09
As I want to use a Linksys WUSB11 adapter I was advised to use NDIS Wrapper.

Using Adept (Package Manager) I have installed NDSIS Wrapper utils but cannot see how to utilise this facility.

Adept's details say it is installed under section 'Misc', I do not appear to have any 'Misc' section on my desktop at all. It also gives the impression that the kernal has the necessary configuration to run NDIS Wrapper without any further additions.

Am I missing something :confused: 

Geffers

---

### Post by John.Michael.Kane on 2006-03-09
[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto)

---

### Post by Geffers on 2006-03-10
[QUOTE=SD-Plissken][https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto)[/QUOTE]

It says " With out any access you can still install ndiswrapper-utils from the install cd but ndisgtk is not on the disk. Put the disk back in the drive, open up synaptic from System>Admin and search for ndis. If you do not know how to install apps, click on the lifepreserver on the top panel and read Ubuntu X.XX starter guide "

How confusing is that - ndisgtk is not on the disk but put the disk back in and search for ndis.

I'm not sure if that means it is on the disk or it isn't :confused: 

Geffers

---

### Post by az on 2006-03-10
Well, if you are not on the net, you cannot download ndisgtk....


You can configure ndiswrapper via the command line for now.  Find your windows driver .inf file and copy it and the other files with it to your Desktop.

Open of a Konsole and type

cd Desktop
sudo ndiswrapper -i filename.inf (Do not type filename, but the name of the real file.)

Type
ls
to show the file names in that folder, since unix is case-sensitive.


Then type
sudo ndiswrapper -l
(that's an "L") to list the ndiswrapper drivers and devices it currently has configured.

If it says you have the driver and the hardware present, load th module

sudo modprobe ndiswrapper

and then go to the KDE network configurator thing and configure your wireless card.

If everything workds, you will need to make the ndiswrapper module load every time you boot by adding it to to the end of the list in the /etc/modules file.  You need to write to this file using sudo

sudo kate

---

### Post by Pnut on 2006-03-10
[QUOTE=Geffers]It says " With out any access you can still install ndiswrapper-utils from the install cd but ndisgtk is not on the disk. Put the disk back in the drive, open up synaptic from System>Admin and search for ndis. If you do not know how to install apps, click on the lifepreserver on the top panel and read Ubuntu X.XX starter guide "

How confusing is that - ndisgtk is not on the disk but put the disk back in and search for ndis.

I'm not sure if that means it is on the disk or it isn't :confused: 

Geffers[/QUOTE]


ndisgtk is a graphical frontend for ndiswrapper you should see it in synaptic package manager just above the ndiswrapper utils.  now the reason that ubuntu is asking for your cd is becase you have the ubuntu cd repository enabled.  i deleted that particular repository just to prevent ubuntu breezy from asking me for the damn cd.   if you search synaptic for ndis....and you have all your repositories installed.....you should find ndisgtk in there....which then u can just mark for installation and install.  i dont use the gui in breezy much because i rather use the command line to do everything.  Now if u want instructions on how to install your wireless device drivers using the command line....gimme a shout.  otherwise have fun using the gui and let me know how it turns out :)

Pnut

---

### Post by Geffers on 2006-03-11
Thanks for all the replies, I have managed to get an ethernet cable connection now so ndis wrapper remedy not urgent but I will persist.

I'm currently on Windows so will now log off and try Linux :-))

Geffers

---

### Post by insub2 on 2006-03-24
[QUOTE=azz]
and then go to the KDE network configurator thing and configure your wireless card.[/QUOTE]


what KDE network configurator thing?  how does one get there?

---

