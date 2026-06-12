---
title: "Ubuntu in an Internet Cafe"
date: 2007-10-23
forum: Desktop Environments
---

### Post by Dzenhax on 2007-10-23
The reason I'm writing is that I've been doing volunteer work at a church here in North Carolina.  They are entirely on Windows Clients.  The Church wants to start an internet cafe and I'm setting up two computers with Ubuntu for the clients.  I think this will be a cool way for folks to be introduced to Linux.

    What I'm asking for are suggestions on the best way to set it up.  Basically I want the user to surf the Internet and that's it.  They should be able to view streaming video and music as well as print, but save nothing to the hard drive.  Floppies, USB flash drives and CDs should be accessable to the Internet user to save work on.  Other than that the user should be as limited as possible.

    I need to lock down the desktop against changes.  I've thought that making the desktop read only would accomplish this.  Will that cause something to crash?

    Also, since it's a church, they want to block adult sites.  Windows has the content filter for this, but I don't know how to do it in Ubuntu.  I tried to do research online, but couldn't find anything about it.

     If you know of a good site that talks about these things I don't mind doing my own research.  Also if you think of things that would make this better for users then let me know about that too.  The last thing I want to do is screw it up and hear "It's not as good as Windows".

Thanks in advance for any help.

---

### Post by midnightracer on 2007-10-24
Hey man, I think its real cool what you're doing for that church.I dont have experience in much of what you said, so I cant really give you tips from experience, but for the adult internet site you should just be able to set up a filter system through firefox. I may be wrong on that, but it may just be that simple.

---

### Post by raeb on 2007-10-24
Found a thread on these forums with a couple of links that may get you started:

[http://ubuntuforums.org/showthread.php?p=3548042](http://ubuntuforums.org/showthread.php?p=3548042)

Hope that helps.

---

### Post by Prospero2006 on 2007-10-24
Hello there,

I'm a middle school teacher in San Antonio, Texas. I've recently installed Ubuntu in about 5 computer labs. (You'll find some people will be very resistant to using it once you get the access set up. Very true.) 

I'm working on a website that describes the work I've done in implementing the classroom setup so that it is safe, secure, stable, and uniform across the board; however, the site isn't done yet. So, I'll point you to my school page first.

[http://www.neisd.net/imak](http://www.neisd.net/imak)

Now, I have something like 400 + kids using Linux right now, and they haven't truly messed anything up yet. It's not easy, but it can be done. Here are some suggestions:

1.) Public Fox Firefox extension.
        This extensions allows you to lock down firefox so users can't
         get in and mess with the options. It also allows you to control
         what file types are allowed to be downloaded. (ie. you can block .exe
         files or zip files.) It also has website blocking.

2.)  Kiosk Tool:
          I only have kde installed in the labs right now because I didn't pilot Gnome.
          Kiosk tool does a very nice job in locking down the desktop. It's not perfect, 
          but with  a few 'chmod a-w /directory' commands, or chmod a-x 'file' mixed 
          in you can really put a deadbolt on desktop and system changes.

                  ie.
```

chmod -R a-w /home/user/Desktop
chmod a-x /usr/bin/passwd

```

3.) Distribute the system with nc and dd:
        If you have identical hardware, you can put a whole lot of time into
        making one computer just right. Then you can export that image to
        other similar computers by booting clients to knoppix and exporting the
         image like this:
```


Host Computer with Master OS
dd if=/dev/hda | nc ip.address.of.client 9000
(/dev/hda points to local hard drive. SATA drive are sd devices)

Client:
nc -l -p 9000 | dd of=/dev/hda


```

Wait two hours and presto. You have two identical operating systems.
(I exported a 3 separate images to over 150 computers like this over the summer
of 2007. It makes big jobs like an internet cafe a snap)

4.) Use passwordless authentication over ssh to make your life easier in the future.
            -Use ssh-keygen -t rsa to generate a public/private keypair on the master  
             system. 
             -Copy id_rsa to /home/user/.ssh/   (Master Machine)
             -Copy id_rsa.pub to /home/user/.ssh/authorized_keys (Clients)  
             -Tweak /etc/ssh/ssh_config to allow RSAauthentication if necessary.
             -You should be able to ssh from one machine to another without a password
              after this. 
             -Give all of your machines sequential ip_addresses. 
             -Write a script like this to reboot the whole lab at once.

```


ipaddy=1
until [ $ipaddy -eq 30 ]
do
  ssh 10.43.231.$ipaddy 'reboot' &
ipaddy=$(($ipaddy +1 ))
done

```

You can write scripts to shutdown, eject cd drives, install programs, 
the sky is the limit. 

5.) Run one computer that acts as a master server for things like samba, apache,
squid, tunnel access, you name it. This computer should run 24/7. 
          -Definitely run a samba server here.
          -Set the clients up so they all mount /mnt/shared (or something)
           at boot time by adding the appropriate entry to fstab.
                    -I add mount -a to /etc/rc.local just to be safe.
          -Then you can do things like point the kdm,gdm, and desktop
           backgrounds files on this shared drive. Change the picture in
           that one central location and the wallpaper changes for the whole lab.
           (Pretty cool.)

-Setting up a Ubuntu lab is challenging for many reasons. (Some people just don't like it for one. Once you get running you'll find that out.) However, it's an awesome, beautiful thing once everything is clicking.

Pros
[http://www.neisd.net/imak](http://www.neisd.net/imak)
[http://tw.neisd.net/webpages/jbeck](http://tw.neisd.net/webpages/jbeck)
[http://www.imakmud.com/](http://www.imakmud.com/)

---

### Post by jespdj on 2007-10-24
I have personally no experience with this, but I know that the GNOME desktop can be locked down, see the guide:
[Desktop Administrators' Guide to GNOME Lockdown and Preconfiguration](http://library.gnome.org/admin/deployment-guide/)

---

### Post by pbcartwright on 2007-10-24
I'm surpised no one came up with the easiest solution to implement... Ubuntu Christian Edition ( Ubuntu CE). It comes complete with dansguardian, internet filter, and firefox Whatwouldjesusdownload toolbar.. check it out here:
[http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/about-ubuntu-christian-edition.html](http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/about-ubuntu-christian-edition.html)

---

### Post by Dzenhax on 2007-10-24
Hey guys,

     Thanks for all these.  It's more than I'd hoped for.  Keep the info comming.  Sorry to hear that some at the school were resistant to Linux.  Hope it's gotten better.

---

