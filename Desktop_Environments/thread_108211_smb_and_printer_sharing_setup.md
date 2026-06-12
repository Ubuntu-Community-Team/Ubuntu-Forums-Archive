---
title: "smb and printer sharing setup"
date: 2005-12-25
forum: Desktop Environments
---

### Post by tdg on 2005-12-25
Hello everyone,

At home, I have a LAN connection between a Windows machine and a Ubuntu machine. With Ubuntu, I have no problem seeing  Windows' shares(through samba), but I can't figure out how to make the Windows machine see the Ubuntu machine(When I do a setup with the System->Administration->Shared Folders, it keeps asking a password whenever I try from the windows machine, I don't want to enter any password)

Also, I got a printer in the Ubuntu machine. How can I 'open' the printer, so that I can print from the Windows machine too?

---

### Post by sciurus on 2005-12-25
Are you using Samba or NFS to share from System->Administration->Shared Folders? I think that either way, you're going to have to put in your username and password to access that share from another machine. It sounds like you'll need to configure Samba manually. See the [HOWTO]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/"). An unauthenticated share could be as simple as:
[data]
comment = Data
path = /path/to/shared/data
read only = no
guest ok = Yes

Sharing a printer with Samba is a little tricker. It might be easier just to use IPP.

---

### Post by sappman2 on 2005-12-26
I was having the same issue. I'm a newbie to Linux. (Ubuntu on home PC, Windows ME on wife's laptop, XP on work laptop)

Here's what  found to be the key alterations to make in the SMB.CONF file:
First, type "sudo gedit /etc/samba/smb.conf" in a terminal. (enter your login password)

I'm assuming that, iunder "GLOBAL" settings, you have the Samba domain set up with the exactly same name as you have in your windows networking "work group" on your windows PC.

Under "AUTHENTICATION" settings, make sure your line for security reads "security = user username map = /etc/samba/smbusers " if you are assigning a secure login name/password for the connection, otherwise you could just set it to "security = share" for a non-secure way to share files/printers. 

Under "Printing" catagory, be sure to set your "load printers =" to yes, making sure you un-comment the line (remove semi colon). Un comment the "printing = cups" and "printcap name = cups" lines.

Next, IMPORTANT***, under the "MISC" settings, find the "Domain Master" setting. It defaults to "Auto".. change that line to read "domain master = yes". Here's why it's important---According to this website: [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/")
Samba must be configured as the domain master when used as a stand-alone server on windows networks NOT using Windows NT domain services. This setting was what finally made it work for me, as I'm on a stand-alone network at home with no domain to log in to.

Finally, under the "SHARE DEFINITIONS" settings, make sure you find the set up for "printers" like this:
[printers]
   comment = All Printers
   browseable = yes
   path = /tmp
   printable = yes
   public = yes
   writable = no
   create mode = 0700

Now that you're done altering the *.conf file, run "sudo testparm /etc/samba/smb.conf" and check for warnings. Then run "sudo /etc/init.d/samba restart". Finally, the last step, log-in to your Windows box.

Doing this *should* make your Samba server visible in your network simply by browsing. If it doesn't appear right away, try clicking (on your windows pc) <START>, then <RUN>, then type in "\\server_computername", and it should take you to whatever home directory was created for the user logged in on the Windows PC as long as it's also set up as a user with the same password in the Samba file "etc/samba/smbusers" and as users on your Samba machine itself. For more help with users/passwords and their permissions, be sure to read through this: [http://www.ubuntuguide.org/#sambaserver]("http://www.ubuntuguide.org/#sambaserver")

Hope this helps! Once you get it set up, it will work seamlessly. Be sure to get the windows printer drivers for your Samba server printer installed on your Windows machine.
`Chris

---

### Post by PhilOSparta on 2005-12-29
Thanks!  Nice Work!  That's exactly what I needed to set up my i386 Breezy box as a printer server for my AMD 64 box that can't drive my Epson Stylus Photo 1200 printer.

---

### Post by charles woodward on 2005-12-30
I've been struggling on and off for weeks with printer sharing - your advice solved it in one - plus sorted out a few problems with networking generally  - thanks for your clear advice.

---

### Post by fishfillet on 2006-01-01
here's my share on ubuntu printer sharing: [http://gerona.gov.ph/davidjr/?p=57](http://gerona.gov.ph/davidjr/?p=57)

I hope it helps!

---

### Post by sappman2 on 2006-01-01
Thanks Fishfillet... there's more than one way to skin a Samba. I think this is why I love Ubuntu: Neighborhood support. (well, that and it just works!) I'm learning more all the time.
-Chris

---

### Post by bdd4 on 2006-01-04
EUREKA! - THIS WAS THE SOLUTION! - IT WORKS LIKE TEXTBOOK!
 too followed this and it worked great! - thank you !

bdd4

---

