---
title: "can not open Access with mdbtools package"
date: 2009-01-19
forum: General Help
---

### Post by said76 on 2009-01-19
Hi,

I have a hard time in getting to open up my Access .mdb files from Ubuntu 8.10. What i did was I received the following message 

could not display smb://homeserver/
There is no application installed for this file type

even with mdbtools package already installed using synaptic manager. Just wonder if there would be anything else need doing in order to get this to work.

My aim here is to be as much familiarised with Ubuntu as possible before starting to make a full commitment to make a move from Windows to Ubuntu. The main applications that we use most of the time are Access and AutoCAD. I'm very grateful if anyone would like to share their ideas or advices on running CAD application on Ubuntu as well. 

Any helps would be greatly appreciated.

Thank you

---

### Post by mbeach on 2009-01-19
Are you trying to use MS Access files stored on "homeserver"?  If so, are you accessing them from your Ubuntu machine?

Seeing the "smb://homeserver/" leads me to believe that homeserver is your Windows machine - is that correct?  If it is, try "smb://ipaddressofhomeserver" for example: "smb://192.168.0.103"

If that doesn't work, you may need to install a samba client.  You can install that through synaptic (System -> Administration -> Synaptic Package Manager), or through the command line with ```
sudo apt-get install smbfs
```.

Then try your smb://.... line.

a better reference than my post:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Good luck,
mb.

---

### Post by said76 on 2009-01-22
Hi MBeach,

Thank you for your reply.

Yes, you are correct. It works using the IP address of the server rather than using the domain name like "homeserver".

However, strangely, it did not load the .mdb file using the openoffice database but rather openoffice writer.

Are there any reasons for that to happen?

Thank you in advance

---

### Post by mbeach on 2009-01-24
Does this post assist you at all?
[http://salahuddin66.blogspot.com/2007/09/mdb-file-in-openofficeorg.html](http://salahuddin66.blogspot.com/2007/09/mdb-file-in-openofficeorg.html)

As for the ip address vs hostname, I believe you might find a bug report like the following of interest:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/235560](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/235560)

From that the first thing I'd try is uncommenting the line in /etc/samba/smb.conf for setting the "name resolve order".

Good luck,
mb.

---

### Post by MatMan on 2009-02-04
I am using intrepid ibex and open office 3.01. I have the packages mdbtools and mdbtools-gmdb installed and cannot open MSAccess files. Even using the links you have posted, mbeach. I get no option under "connect to an existing database" to choose MSAccess. Any hints? I tried connecting via ODBC and Adabas D just in case and no glory there either.

---

