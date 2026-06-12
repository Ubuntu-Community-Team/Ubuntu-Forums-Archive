---
title: "Exchange 2007"
date: 2007-08-07
forum: Desktop Environments
---

### Post by dushkal on 2007-08-07
Hi,

Recently our corporate environment was updated to Exchange 2007. Unfortunately, our dear unstable Evolution does not work with it.....:(

I've been searching the net for the Evolution support, have considered many options:

1. Run OWA that comes with the new server, forget about mail application...
2. Run IMAP on the exchange - one disadvantage is that I would completely miss the calendar functionality
3. Try and compile OpenChange plugin and connect using that (if that is at all possible) but unfortunately,this means that again treading into unknown fields of compilation etc (e.e. OpenChange requires libmapi which requires pidl....this can go on for a while....) and again even after this if OpenChange can connect or not is a big mystery...
4. Run Outlook 2003 using Wine..

Now the question:

Can anyone think of any other alternative to check mails and appointments from Exchange 2007 server?

Thanks,
Dushkal

---

### Post by phidia on 2007-08-07
Have you read [this]("http://ubuntu-tutorials.com/2006/10/24/use-evolution-with-microsoft-exchange-ubuntu-606-610/") tutorial? 
It came up on a search of evolution-exchange. Hope it's helpful.

---

### Post by dushkal on 2007-08-07
Yes. It was perfectly working (well, perfect as in the perfect world we live in...) with Exchange 2003, but stopped working with 2007.

My doubt is that this problem is due to the fact that Evolution uses OWA to access the exchange than MAPI.

---

### Post by tomrules345 on 2007-08-07
"Can anyone think of any other alternative to check mails and appointments from Exchange 2007 server?"

Well im not sure if anyone can help you with that but i do have many suggestions for a mail server running on linux that you could try to move your office over to......

---

### Post by dushkal on 2007-08-08
Thanks....unfortunately such decisions are taken on a much higher level which I can not influence....currently I'm using OWA with Firefox. I plan to install Outlook 2003 with Wine over the weekend till a solution is available

---

### Post by troelskn on 2007-10-23
I run Outlook in VMWare. It works, but I'd much rather use a native application. OpenChange would be a relief. Even if it's in alpha stage, it's still better than nothing. If anybody knows how to compile the thing for Ubuntu 7.10, I would be grateful.

---

### Post by negiscallion on 2007-10-24
I would be very interested as well in learning how to compile it in Unduntu. You can get the rpm's of the preview version to work with evolution 2.12. However, the 0.1 evolution plug-in can only handle email messages and lazily at that.

1) Install the 0.4 mapi library and 0.1 exchange plugin by using alien to convert them to .deb files, and then installing them.

2) The exchange plug-in was built for evolution 2.8 but that only effects the install location of the plug-in modules. Copy the two files appropriate files from /usr/lib/evolution/2.8/plugins

liborg-gnome-openchange.so
org-gnome-openchange-plugin.eplug

to /usr/lib/evolution/2.12/plugins. Then, edit the eplug file so that it references the correct location of the library. Change the "location" attribute of the "e-plugin" tag in that file to

/usr/lib/evolution/2.8/plugins/liborg-gnome-openchange.so

Finally, the library was compiled against different versions of the camel libraries. Create the following links in /usr/lib:

libcamel-1.2.so.0 -> libcamel-1.2.so
libcamel-provider-1.2.so.8 -> libcamel-provider-1.2.so.10

I *think* that was all.

---

### Post by troelskn on 2007-11-06
Thanks for the tip on **alien**. Did you try getting the newest release (holodeck) running? If so, which RPM's did you start from?

---

### Post by dushkal on 2007-11-08
> **negiscallion said:**
> I would be very interested as well in learning how to compile it in Unduntu. You can get the rpm's of the preview version to work with evolution 2.12. However, the 0.1 evolution plug-in can only handle email messages and lazily at that.

1) Install the 0.4 mapi library and 0.1 exchange plugin by using alien to convert them to .deb files, and then installing them.

2) The exchange plug-in was built for evolution 2.8 but that only effects the install location of the plug-in modules. Copy the two files appropriate files from /usr/lib/evolution/2.8/plugins

liborg-gnome-openchange.so
org-gnome-openchange-plugin.eplug

to /usr/lib/evolution/2.12/plugins. Then, edit the eplug file so that it references the correct location of the library. Change the "location" attribute of the "e-plugin" tag in that file to

/usr/lib/evolution/[COLOR="Red"]2.8/[/COLOR]plugins/liborg-gnome-openchange.so
[COLOR="Blue"]I think you meant 2.12 here...[/COLOR]
Finally, the library was compiled against different versions of the camel libraries. Create the following links in /usr/lib:

libcamel-1.2.so.0 -> libcamel-1.2.so
libcamel-provider-1.2.so.8 -> libcamel-provider-1.2.so.10

I *think* that was all.

[COLOR="Blue"]
OK, did all these things.....went fine...

Additionally libedataserver-1.2.so.7 is also referred, so additional linking to

libedataserver-1.2.so.7 -> libedataserver-1.2.so.9.1.0

in /usr/lib is needed.....

Now I can enable the plugin...See here:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=49503&stc=1&d=1194515744[/IMG]

BUT, I do not see OpenChange as a Server type...

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=49504&stc=1&d=1194515744[/IMG]

as opposed to the one posted on the OpenChange site...

[IMG]http://www.openchange.org/images/openchange/evolution/new_account_gimp.png[/IMG]

Anybody??
[/COLOR]

---

### Post by negiscallion on 2007-11-13
You are probably experiencing issues related to the plug-ins being linked to different/missing libraries. You will have to look at the Evolution debug output to troubleshoot it. Even if you get it working, the packaged version of the openchange evolution plug-in only handles emailing, unfortunately. 

I have managed to massage the current development tree and the newest released libmapi into compiling. However, the last time the evolution plug-in was touched was back in July (according to the websvn commit log). As such, it does not seem to be in a completed state and/or does not work with the new libmapi. I intend to keep poking at it so long as I do not get frustrated. Even though I have no plans to develop against it, I will let you know if I get anything working.

The command line libmapi client works great though ;^).

---

### Post by chadders on 2007-11-20
Believe me there is more than one person looking for an answer. Exchange 2007 will not be supported by Evolution until version 2.14. I'm looking for alternatives as I have the unfortunate duty of migrating the company I work for to Microsoft Exchange.

---

### Post by hugoheden on 2007-11-20
Check out evolution-brutus, which contains two main components: 

o) An Evolution plugin, that would be responsible for connecting to...

o) a Windows-server, that would act as a proxyserver for the "real" Exchange server, communicating with the latter using MAPI

-- if I understand correctly (which is, of course, highly unlikely).

evolution-brutus supposedly supports Exchange 2007. I've taken a quick look at it, but not tested it. The main drawback seems to be that one needs a Windows box to run it on. Some of you may be able to convince your IT-departments to try this out, for the benefit of Linux-users on the company. (I've tried running it on my own lap-top with Windows XP under VMWare but did not succeed)

Best regards 

Hugo Heden

---

### Post by HDave on 2007-11-29
Historically, Microsoft has made it near impossible to create a software product that acts as a client to exchange.  While its easy to blame this on their closed nature, its more likely that they simply never justified the expense of creating, documenting, and maintaining an open API.

In Exchange 2007, it appears as though they have reversed their previous stance and created a well documented open web services API.   

[http://msdn2.microsoft.com/en-us/library/bb204119.aspx]("http://msdn2.microsoft.com/en-us/library/bb204119.aspx")

I know it will take work, but there is now no technical reason why the open source community can't create a killer exchange client that doesn't rely on flaky screenscraping technology.

I sure hope that when evolution supports exchange 2007 they'll use this API...or perhaps someone could write a new Thunderbird plug-in for email (and calendar) that uses this API.

Then no more outlook...then no more windows on my desktop.

---

### Post by dustobub on 2007-12-04
Well after two days of trying to find a decent way of accessing my hosted Exchange 2007 account I finally found a decent solution. I tried just about everything, Evolution which doesn't yet work with Exchange 2007, a Windows XP Virtual Machine with Office 2007 which was too slow, to using Outlook Web Access through Firefox. OWA was okay but since I was using Firefox I couldn't use the premium client which is far superior to the light client.

I thought of using Internet Explorer through wine so I downloaded ie4linux which installed  ie6. The only problem though is that it uses a Windows 98 bottle which is not compatible with OWA Premium even though ie6 is. If you try to change the bottle to Windows 2000 or XP, you lose access to HTTPS sites, which of course OWA is typically. 

It dawned on me today that I could possibly fool OWA by changing my user-agent string in ie6, and it worked! If you add these two lines to user.reg in .ie4linux, you will be able to use the premium OWA client in ie6. 

[Software\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\User Agent\\Post Platform] 
"Windows NT 5.1"="This String Doesn't Matter I think"

[Software\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\User Agent\\Pre Platform] 
"Windows NT 5.1"="This String Doesn't Matter I think"

PS - There should be no space in the word "Internet" like it shows, I'm not sure why it does this.

So far things are working fine, I turned off all of the toolbars in ie6 and it almost feels like Outlook. I am extremely happy with this and I can finally have the best of both worlds, Outlook with Exchange, and Linux. 

Might be worth it to start a new thread with this info because I have yet to see anyone be able to get OWA Premium working in Linux.

Dustin

---

### Post by HDave on 2007-12-05
I like the idea of OWA in IE over wine, but I need offline capability.  Plus I keeping reading about wine's instabilities.

For myself, I got vmware working with an XP guest and installed outlook.

A little slow, a little inconvenient, but at least I am up and running...without having to natively boot windows...   Here's looking forward to version 2.14 (???) of Evolution and support for Exchange 2007 through web services.

---

### Post by DrOlaf on 2008-01-16
I just followed dustobob's method and it worked a treat with my university's Exchange 2007 server. Two things, though:

1. The current version of wine [0.9.53 at the time of writing] has some problems with displaying the text in IE6's menus, so I downgraded to 0.9.51 as per [this thread]("http://ubuntuforums.org/showthread.php?t=665786") and it worked fine.

2. I forgot to set the bottle to Windows 98, but the default Windows 2000 settings worked OK for me anyway once I'd pasted the registry entries in from dustobob's email. 

This is great! One less reason to dual-boot.

---

### Post by RichTJ99 on 2008-02-11
> **dustobub said:**
> Well after two days of trying to find a decent way of accessing my hosted Exchange 2007 account I finally found a decent solution. I tried just about everything, Evolution which doesn't yet work with Exchange 2007, a Windows XP Virtual Machine with Office 2007 which was too slow, to using Outlook Web Access through Firefox. OWA was okay but since I was using Firefox I couldn't use the premium client which is far superior to the light client.

I thought of using Internet Explorer through wine so I downloaded ie4linux which installed  ie6. The only problem though is that it uses a Windows 98 bottle which is not compatible with OWA Premium even though ie6 is. If you try to change the bottle to Windows 2000 or XP, you lose access to HTTPS sites, which of course OWA is typically. 

It dawned on me today that I could possibly fool OWA by changing my user-agent string in ie6, and it worked! If you add these two lines to user.reg in .ie4linux, you will be able to use the premium OWA client in ie6. 

[Software\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\User Agent\\Post Platform] 
"Windows NT 5.1"="This String Doesn't Matter I think"

[Software\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\User Agent\\Pre Platform] 
"Windows NT 5.1"="This String Doesn't Matter I think"

PS - There should be no space in the word "Internet" like it shows, I'm not sure why it does this.

So far things are working fine, I turned off all of the toolbars in ie6 and it almost feels like Outlook. I am extremely happy with this and I can finally have the best of both worlds, Outlook with Exchange, and Linux. 

Might be worth it to start a new thread with this info because I have yet to see anyone be able to get OWA Premium working in Linux.

Dustin

Hi,

I am also very interested in this.  I am using Crossover & I was curious how to make a Reg edit on my Win98 bottle with IE6?

EDIT:  I cant get to the Regedit window, but I cannot find those reg edits listed above.  I am unsure if I should be making the entire key.  Then I am not sure if its HKLM or HKLU (or both).

Thanks,
Rich

---

### Post by HDave on 2008-02-29
They have exchange 2007 support on the Gnome roadmap now.  Check it out:

[http://live.gnome.org/RoadMap]("http://live.gnome.org/RoadMap")

Unfortunately it is not slated until Gnome 2.24 which means it won't be in Hardy.  :(  What a drag....

EDIT:  The evolution developers (many of whome are great bloggers) are saying that support for exchange should be available soon even though it will be too late for Hardy.   

[http://blogs.gnome.org/sragavan/2008/01/21/evolution-mapi-exchange-2007-preview/]("http://blogs.gnome.org/sragavan/2008/01/21/evolution-mapi-exchange-2007-preview/")

---

### Post by RichTJ99 on 2008-03-20
I have a Pentium M laptop that is a little slow on XP + Outlook & would be perfect as a full time Ubuntu machine.  Unfortunately the lack of a good way to use Exchange 2007 is kicking me in the butt.  

I think that Ubuntu would be great on this little guy (which tends to sit up for 7-10 days without rebooting in XP).  Its just an email machine in a nice location at home. 

I am eagerly waiting for this to work!

---

### Post by Ghilteras on 2008-04-15
hi there, i'm bumping this old thread because i'd like to know if anyone tried to comppile/install openchange on ubuntu (i'm running the hardy beta)

i have some problems compiling its source (after installing samba4 i got ndr dcerpc and samba-config packages not found during limbapi configure) and it seems there arent any *deb packages for the latest version of libmapi 0.7

any clue would be most welcome since i need to use a mail client on exchange 2007 (at work they have just migrated from exchange 2003 to exchange 2007, so goodbye exchange connector) 

i can use the OWA in firefox or imap with thunderbird but this way I cant display my additional mailboxes, so i'm stuck to fallback again to windows to work properly.

---

### Post by HDave on 2008-04-15
@Ghilteras -- I assume you are trying to compile openchange's libmapi and Samba4 in an effort to get the new evolution mapi provider going.  Is this right?  If so, and you succeed, you will be the hero of this thread!

I myself haven't tried to compile it, but I found a link to an ftp site (from one of the evolution programmers) where there are packages for this put together for fedora 8 and suse 10. 

[http://download.opensuse.org/repositories/home:/jjohnny:/evolution-exchange-mapi-provider/]("http://download.opensuse.org/repositories/home:/jjohnny:/evolution-exchange-mapi-provider/")

Looking into the Fedora directory I found packages for libmapi 0.7, samba 4, and the mapi provider (as of April 11th).

I am in over my head here, but could one use alien to convert the rpm packages to deb?  

Hope this helps...   If not, heres a link the aforementioned programmer's blog...maybe he can answer your questions:

[http://johnnyjacob.wordpress.com/2008/01/20/evolution-mapi-provider-preview-builds/]("http://johnnyjacob.wordpress.com/2008/01/20/evolution-mapi-provider-preview-builds/") 

Good luck!

---

### Post by Ghilteras on 2008-04-17
hey there.

i successfully installed the rpm packages from open suse after converting them to *deb with alien

it seems that those packages were built for evoltion 2.12 (gutsy) while i'm using the hardy version (2.22), and I got into foreseeable library problems after starting evolution, so i copied the library files for the openchange evolution plugin into the 2.22 path and the errors disappeared.

if i start evolution from command line and go into plugins as i try to enable/disable openchange i only see a debug message that says "exchange mapi enabled/disabled" or "openchange enabled/disabled" thus so far everything seems to work

the problem is that if i try to create a new mail account i can't see openchange in the list of connectors, looking in the command line i just get a warning on the camel libraries, nothing else.

in the end it appears it's impossible to use openchange on the latest evolution, i should try with the 2.12 version as soon as i have a bit of time, or wait for fedora/suse packages of openchange for evolution 2.22

that's all for now if anyone managed to go further please share with us.

---

### Post by HDave on 2008-04-26
@Ghilteras

Can you tell me what you did to install them and I will try to duplicate on my system.  

I see three packages available for download, and I have three questions:
    1) the mapi provider (is this also the evolution plug-in...or is the a seperate thing??)
    2) something about 'phaser' (what is this??)
    3) a samba 4.0 alpha (please tell me this doesn't depend on an alpha of samba!!!)

Thanks for any guidance you can provide.

---

### Post by Ghilteras on 2008-04-28
you need to install 3 packages:

samba4
libmapi
evolution mapi connector


first you need to install samba4 then libmapi and last the evolution plugin.

i tried to install them on evolution 2.22, i'm using ubuntu 8.04 but no luck with the rpms (i wanted to convert them to *deb package with alien) because the libmapi rpm cannot be migrated to deb

so i fetched the sources but the libmapi make fails here:

Compiling libmapi/IProfAdmin.c with -fPIC
In file included from /usr/local/samba/include/credentials.h:132,
                 from libmapi/IProfAdmin.c:23:
/usr/local/samba/include/credentials/proto.h:410: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘principal_from_credentials’
make: *** [libmapi/IProfAdmin.po] Error 1


i'm currently stuck here.

regards

---

### Post by dushkal on 2008-05-07
well, I had not considered one more possibility...:) 

My laptop is a dual boot between Windows and Ubuntu (Hardy). So, I just installed VMware Workstation, and now using my windows partition as a VM. Hopefully I will never boot into Windows now as all the functionality I needed from Windows can now be accessed through this VM.

So, for now I am happy, now even if the Exchange 2007 support is delayed by another year, I can live with it....

---

### Post by RichTJ99 on 2008-05-14
Can this work using Virtual box?

---

### Post by Ghilteras on 2008-05-14
there should not be any need to use virtual machines, soon enough openchange plugin will be released alongside the new evolution

it's already present in the beta 2.23 version, there arent *deb packages and it's very hard to compile it from source but people from suse/fedora testint their rpms report a working feedback

it's just a matter of time

---

### Post by dushkal on 2008-05-19
> **Ghilteras said:**
> it's just a matter of time

I've been hearing this since past one year, that the plugins are available for SuSE and/or Fedora, but I have not seen any 'working' thing for more than one year, and then only I thought of using VM. The first time I searched for it, was more than a year ago actually: 

[http://www.mail-archive.com/evolution-list@gnome.org/msg05470.html](http://www.mail-archive.com/evolution-list@gnome.org/msg05470.html)

Then after one year. status is almost the same:

[http://www.mail-archive.com/evolution-list@gnome.org/msg08621.html](http://www.mail-archive.com/evolution-list@gnome.org/msg08621.html)

Anyway, I will move to evolution when the plugin is released, but this was the fastest option for me....

**@RichTJ99:**

Yes, I think with VirtualBox also you can use the existing windows partition as a VM, Although I use VMware Workstation, one can also use VB for this. I haven't tried it, but a quick google search lead me to [http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/](http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/)

All the best.

---

### Post by Ghilteras on 2008-05-19
> **dushkal said:**
> I've been hearing this since past one year, that the plugins are available for SuSE and/or Fedora, but I have not seen any 'working' thing for more than one year, and then only I thought of using VM. The first time I searched for it, was more than a year ago actually: 

[http://www.mail-archive.com/evolution-list@gnome.org/msg05470.html](http://www.mail-archive.com/evolution-list@gnome.org/msg05470.html)

Then after one year. status is almost the same:

[http://www.mail-archive.com/evolution-list@gnome.org/msg08621.html](http://www.mail-archive.com/evolution-list@gnome.org/msg08621.html)


look here:

[http://download.opensuse.org/repositories/home:/jjohnny:/evolution-exchange-mapi-provider/](http://download.opensuse.org/repositories/home:/jjohnny:/evolution-exchange-mapi-provider/)

as you can see last update is yesterday, those are buildable sources, try these, they works although they are very hard to build expecially on ubuntu

it's safer to wait for the next version of evolution where the plugin will be enbedded. they should have released it for evolution 2.22, but they didnt make it in time, it's present on evolution beta 2.23 though

---

### Post by limiter on 2008-05-20
Dang, I just installed 8.10 over my windows after doing a really basic search on exchange and ubuntu.  I saw that it was possible but didn't realize my office was on 2007 and that even after a couple years the support still isn't here for it.  I'm looking around at the evolution site but can't seem to find when that next release is happening to support 2007.

---

### Post by kaydo on 2008-05-29
Check [http://www.openchange.org/](http://www.openchange.org/), there are now packages for Debian/Ubuntu which should allow Exchange 2007 connectivity.

Repository is at [http://samba.org/~jelmer/debian/](http://samba.org/~jelmer/debian/)

---

### Post by HDave on 2008-05-29
Looking at the packages in that repository, I see samba4 and libmapi, but I don't see the evolution-mapi-plugin.  I believe this is required to get evolution to talk to exchange 2007.

Edit:  Those are also packages for Debian Sid and won't work on Hardy...got myself part way into library hell before successfully backing out. :(

---

### Post by HDave on 2008-05-29
@Ghilteras

I downloaded the Fedora 9 packages from the evolution daily builds, used alien to convert them to debs and installed them successfully.  They appear to be for evolution 2.22 and they install fine.  When I run evolution I see the MAPI plug-in in the list of plug-ins.

However, I cannot create an account that uses MAPI as an account type.  Running evolution from the command line I see this error:

```
(evolution:20834): e-utils-WARNING **: can't load plugin 'libmapi.so.0: cannot open shared object file: No such file or directory'
```

I tried copying some of the libraries from /opt/samba4 to /usr/lib/evolution/2.22, but no joy.

Any ideas?  It feels like we are getting close...

---

### Post by dandantheitman on 2008-06-02
Hey HDave,

I had the same problem as you.  you need to link the libmapi.so.0 to libmapi.so in the /opt/samba4/lib.

sudo ln -s libmapi.so libmapi.so.0

Dan

---

### Post by HDave on 2008-06-02
Thanks!  Your suggestion, along with adding /opt/samba4/lib to my LD_LIBRARY_PATH did the trick.  No more MAPI library errors...evolution now comes up and asks me for my MAPI/Exchange password!

However, no matter what combination of domain and username (we are on a domain here) it keeps telling me Login failed.  Will check the server side to see what the log says...but any further thoughts are appreciated.

---

### Post by Ghilteras on 2008-06-03
> **HDave said:**
> Looking at the packages in that repository, I see samba4 and libmapi, but I don't see the evolution-mapi-plugin.  I believe this is required to get evolution to talk to exchange 2007.


*deb packages are only for samba4, libmapi and openchange, no evolution plugin, only the command line client



> However, no matter what combination of domain and username (we are on a domain here) it keeps telling me Login failed. Will check the server side to see what the log says...but any further thoughts are appreciated. 

I'm stuck here as well, i'm chatting on the devel mailing list with the developers and they said:

[i]I have found another explanation which makes more sense. Maybe your Administrator has blocked MAPI connections and require you to use either RPC over HTTPS or OWA.

If you have an Outlook client running, try to create a new profile using default authentication (no rpc over https etc.). If Outlook refuses to launch/work, then openchangeclient won't do the trick either. If Outlook does work, then I'll probably be able to figure out the issue you face and fix whatever is necessary.[/i]

you may try to check this, any feedback would help the progress. moreover you can try the command line opechange and see if it works:

$ mapiprofile --database=/tmp/profile.ldb --profile=myprofile 
 --username=myuserid --password=mypass --address=127.0.0.1
 --domain=mydomain --create 

where address is your exchange server, you should get this output

Profile myprofile completed and 
 added to database /tmp/profile.ldb


then you list it:
 
$ mapiprofile --database=/tmp/profile.ldb --list 
We have 1 profiles 
in the database:
        Profile = myprofile

set it to default:

$ mapiprofile --profile=myprofile -S 
Profile myprofile is now set 
the default one

try to connect:

$ openchangeclient
    

if you get:

MapiLogonEx              : MAPI_E_NETWORK_ERROR (0x80040115)


then you have my very same problem :)

cheers

---

### Post by HDave on 2008-06-03
@Ghilteras -- Following your instructions I was able to get it to work.  Here's a couple things though:

1) I had to create a new mapi profile database which I did via:

```
mkdir ~/.openchange
mapiprofile --newdb
```

Which creates a new profiles.ldb file.

2) No matter what command I run, I always see the following:

```
<cmd>: /lib/libpopt.so.0: no version information available (required by <cmd>)
```

where <cmd> = mapiprofile, openchangeclient, mapitest, etc. 

However, it doesn't seem to break anything.

3) When I created my profile, mapiprofile command seg faults.  However the profile was created and I was able to continue.  Don't know why this is.

4) Creating the profile adds my windows exchange password to my .bash_history file, so I had to remember to go back in and delete it.

5) I used the mapitest command to verify mapi was correct.  Also used ```
openchangeclient -m
```

6) I needed to link-up three libraries in order to make everything work:
```
sudo ln -s libmapi.so libmapi.so.0
# Needed to run mapitest
sudo ln -s libmapiadmin.so libmapiadmin.so.0
# Needed to run openchangeclient
 sudo ln -s libocpf.so libocpf.so.0
```

Once I did all this, the openchangeclient program worked flawlessly, although it does produce a lot of "Conversion error: Illegal multibyte sequence()" errors.

Towards your specific problem I can add this-- my default settings for Outlook on Windows are to use https.  However, I can change this to a direct connection and everything still works, provided I am inside the network and provide the internal name for the exchange server.  If this works for you too, then you have a problem on the Ubuntu side.  If not, then you need to tweak your exchange server.

I should also say I started with the Fedora 9 rpm packages and used alien on them.  Perhaps there is a difference between those and the SUSE ones.

Once I got to this point, I was able to get the MAPI plugin to evolution working, but it does not seem very robust...but thats another post.

---

### Post by Ghilteras on 2008-06-04
hey HDave, nice you got it working, so there is hope

where can you find your https configuration on outlook client?

i'm trying to understand if my exchange requires https but i just see an option that tells "http tunnel" no https to be found anywhere in the options.

---

### Post by HDave on 2008-06-04
> **Ghilteras said:**
> where can you find your https configuration on outlook client?

In Outlook 2003 (which is what I use) it is located under:

tools->options->mail setup->email accounts->
view or change existing accounts->change->more settings->

connection tab  - check http (you are right no https option here, but...)

security tab - check encrypt (I believe this makes it use https)

Another thing, I could not connect to exchange via the domain name of the server (i.e. "exchange.mycompany.int") I had to use the internal IP address (i.e. "192.168.1.50").

Other ideas to think of:

1) you can ping the exchange server from ubuntu
2) you can use outlook to connect directly (no http) to the exchange server from any windows machine
3) ensure your exchange server is listening on the standard port (sorry don't know which one this is)
4) firewall rules in Ubuntu

good luck

---

### Post by Ghilteras on 2008-06-04
same settings on outlook 2007, i've checked and my client doesnt need any encryption or http tunnel to connect.

i guess i should be able to connect using mapi then.


did you use the rpm migrated to debs with alien or the proper deb packages released on the jelmer ([http://samba.org/~jelmer/debian/](http://samba.org/~jelmer/debian/)) repository?

---

### Post by HDave on 2008-06-04
I couldn't use jelmer's deb packages as I got into dependency troubles with gnutils and other things.  I used alien on the Fedora 9 rpms from the evo-plug site (Johnny's).

Edit:   [http://download.opensuse.org/repositories/home:/jjohnny:/evolution-exchange-mapi-provider/Fedora_9/i386/]("http://download.opensuse.org/repositories/home:/jjohnny:/evolution-exchange-mapi-provider/Fedora_9/i386/")

---

### Post by sweetsinse on 2008-06-04
nice w3rk HDave & Ghilteras.

i have followed your guys procedure and managed to get it working from command line, using the Fedora 9 packages, nice job! i can use the terminal to authenticate, and i can see all my mailboxes and their size/etc.

i can't seem to get the evolution part working though.  i can enable the plugin, i can see it in the 'new' account list, but i am having problems getting the gnome-keyring-daemon/authentication to play nice...  this probably has nothing to do with the plugin but more to do with the fact that i am running XFCE/Xubuntu 8.04.


also, what did you put in for the server part of the MAPI plugin?  my domain is brokerbin.local, my exchange server name is just exchserv (10.0.0.10), and i am using https i believe.  i tried (I have WINDBIND name resolution in /etc/nsswitch.conf):

[https://exchserv](https://exchserv)
[http://exchserv](http://exchserv)
exchserv
[https://10.0.0.10](https://10.0.0.10)
[http://10.0.0.10](http://10.0.0.10)
10.0.0.10

but none work.


$GNOME_KEYRING_PID seems to be null and apparently it shouldn't be?


i tried copying my .openchange/profiles.ldb to .evolution/mapi-profiles.ldb and for a minute i thought it worked, no errors or anything in the terminal, but i cannot see any of my folders.  all i see is junk mail and trash.

any help would be appreciated, i am excited to help get this w3rking awesome!

---

### Post by HDave on 2008-06-04
Once I got the stuff installed, I could see the MAPI plug-in in exchange, but in order to make it work from the menu, I had to add these lines to my .profile file (then logout/login) :

```
# added for exchange mapi support
export PATH=/opt/samba4/bin:$PATH
export LD_LIBRARY_PATH=/opt/samba4/lib:$LD_LIBRARY_PATH
```

Adding these lines to .bashrc made it so it would work from a command line, but not the menu.  From the menu, I could enable MAPI from the list of plug-ins, but it wouldn't stay enabled after I closed the app.  Also, I could pick Exchange MAPI from the list of account types, but it didn't have the textbox to enter a domain....wierd.

I can also tell you I am certain there is no relationship between mapiprofile profiles and evolution...I deleted mine and evolution still works.

Here's what I put in "Receiving" tab of the account editor window in evolution:

Server Type:  Exchange MAPI
Server:       192.168.1.50
Username:     (windows domain user name...eg "jsmith")
Domain Name:  mycompany.int

If I hit the authenticate button, it prompts me for a password, then does nothing (I assume if it failed, it would say something)....again...wierd.

So I can now see my email in evolution.  However, I cannot see contacts or calendar items, nor can I see any of the bodies of emails!  Don't know whats up with that...hoping you guys can get to this point soon and help light the way.

---

### Post by sweetsinse on 2008-06-07
hmm...

well i got it working consistently with the password issue, i have a custom script to start/wmctrl evolution anyway so i added the EXPORTs there.  i am trying to convert my company over to completely linux/ubuntu based workstations and keep a couple of Win servers for multi-remote use only when windows is absolutely necessary for some ridiculous reason.  we have an exchange server 03, so i'd really like to see this working even in beta stages... the OWA tends to have some issues, especially on user with extremely large mailboxes (one user has a 100MB COMPRESSED backup of his exchange SUMMARIES, over 1 million messages).  eventually i will convert the server (back) to linux but that isnt an option for awhile.

also i am implementing exchange server based linux roaming ~/ profiles using pam_mount and loopback techniques across a CIFS share :) works dreamy, im on it now.  will write a doc about that since it took awhile to figure out, esp. with ALL KDE based apps.

anyways, i can authenticate it seems, but all i can see is Junk email and trash.  also, at the to of the mailbox list, right below "New"--where the selected mailbox's name should be, i see (null) instead of Junk E-mail.

still w3rking on it...

---

### Post by HDave on 2008-06-07
> **sweetsinse said:**
> at the to of the mailbox list, right below "New"--where the selected mailbox's name should be, i see (null) instead of Junk E-mail.

Ditto here...am considering pinging the evo-mapi guys at gnome, but its so busted, I must have something screwed up somewhere.  Wondering if it is the illegal converion errors I get from OpenChange....

---

### Post by sweetsinse on 2008-06-08
what version of exchange sever are you using?  2007?  i was in the #evo-mapi channel on gimpnet talking to the devs about my error.  i gave him pastebins for my success from terminal:

[http://pastebin.com/fc9692d6](http://pastebin.com/fc9692d6)

and my non-success from evolution:

[http://pastebin.com/f222d893a](http://pastebin.com/f222d893a)

jony said he had not tried it (evolution-gui) yet with 2003 so that be some of my issue at least, not sure.  i am not getting any errors whatsoever with the openchangeclient though, save the one about needing version information or whatever.  i have tested sending mail, listing my mailboxes, and --fetchmail, all of which seem to work absolutely fantastic.  the fetchmail only took about 15 seconds to dump the ENTIRE CATALOG of messages from my mailboxes, including their full bodies, to the terminal, and i have several thousand emails in my exchange boxes.

at any rate..  its shaping up to be a nice addition to evolution.

---

### Post by HDave on 2008-06-08
> **sweetsinse said:**
> what version of exchange sever are you using?  2007?

Yes, 2007.  I have found the openchangeclient to be very fast as well.  Could be some months though before this whole shebang is ready for prime time.

---

### Post by hggdh on 2008-06-16
A recent thread on the evolution-hackers mailing [list]("http://mail.gnome.org/archives/evolution-hackers/2008-June/msg00042.html") suggests:

1. code is still in flux;
2. there is an issue on licence -- MAPI code is GPLv3, Evo itself is still GPLv2. Until Evo licencing is upgraded to GPLv3, it will not be possible to release the code;
3. the developer (sri) has some doubts if this will be available as of Evo 2.24.

Please keep in mind that you are using code still in development. If you have issues, we will not be able to address them under Ubuntu -- please open a bug upstream in this case ([http://bugzilla.gnome.org/](http://bugzilla.gnome.org/)), but be sure to state you know this is under development.

Of course, you can also mail the evolution-hackers list with what you find.

---

### Post by dmayer on 2008-06-23
Hi,

I seem to have the same problem as sweetsinse. I am trying to connect to a Exchange 2003 server and everything works fine from the commandline, but the evolution plugin just stops after some folders and throws OpenFolder               : MAPI_E_NOT_FOUND 
errors and some other messages at me.

sweetsinse if you or anybody else has any success in getting evolution to work with it, please give us a hint here, thanks!

Daniel

---

### Post by HDave on 2008-07-08
Hate to bail on you guys, but after a significant amount of time playing around with the evolution-mapi-plugin, I have decided to give up and try again in October, when hopefully the first release of this thing is out.  It's still just too green.  Note that I believe the openchange stuff is more solid at this point.

On a more positive note, I went ahead and paid the $65 to CodeWeavers for the supported version of Wine.  Best money I have ever spent.  Unlike regular wine, the CrossOver wine supports Outlook 2003.  So for the past week I have been running Outlook 2003 on CrossOver 7.0 on Ubuntu 8.04 and connecting to my Exchange 2007 server....even encrypted over http!!!

While I will say it is not perfect (I have the occasional oddity) it is 95% solid.  So I am going with this until such time that Evolution can talk solidly with Exchange 2007.

Interestingly, I also see Exchange 2007 support on the roadmap of Thunderbird, which has long been my favorite email client.  So I guess now it's a race!

---

