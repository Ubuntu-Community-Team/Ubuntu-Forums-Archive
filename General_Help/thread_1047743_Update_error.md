---
title: "Update error"
date: 2009-01-22
forum: General Help
---

### Post by rozbarwinek on 2009-01-22
Today I was notified by ubuntu that there are new updates but when I try to install them an error occured:

```
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7

```

W wasn't changing anything since my last update...

---

### Post by dcstar on 2009-01-22
> **rozbarwinek said:**
> Today I was notified by ubuntu that there are new updates but when I try to install them an error occured:

```
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7

```

W wasn't changing anything since my last update...

It means that there is a network problem somewhere, give it a few hours and try again.

---

### Post by kostkon on 2009-01-22
I think the PPAs have now started offering signed packages, so you have to go to this PPA's page on Launchpad to download its key and then add it in your *Software Sources* (i.e. *System &#8594; Administration &#8594; Software Sources*).

---

### Post by rozbarwinek on 2009-01-23
> **kostkon said:**
> I think the PPAs have now started offering signed packages, so you have to go to this PPA's page on Launchpad to download its key and then add it in your *Software Sources* (i.e. *System &#8594; Administration &#8594; Software Sources*).

That's right :)
So I have only Banshee PPA repository and I found that the pgp key is here --> [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x4874D3686E80C6B7](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x4874D3686E80C6B7)
Is there a way that I can add it by terminal like for example VirtualBox key:

```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
```

or I have to download that file and add it manually?

---

### Post by blackgr on 2009-01-23
I made this small bash script. it will check you intrepid system for all launchpad sources and will download and install the keys for you!

Who ever wants this for Hardy. Just edit the script and change intrepid to hardy

edit:
You have to run this with sudo

---

### Post by NNxD on 2009-01-24
Great job, thanks!

---

### Post by Yathi on 2009-01-24
yeah.. really nice.. thanks..

---

### Post by blackgr on 2009-01-24
im glad you liked it :)! After the update you can remove curl.

```
sudo apt-get remove curl
```

---

### Post by stratlonestar on 2009-01-24
NICE! Thank you so much!

---

### Post by befana on 2009-01-25
Sorry for my stupid question, but what to do with this script?
OK, I've found it- run in terminal.

---

### Post by Merkaba_ZA on 2009-01-25
Thanks a lot for the script.  I'm just having a problem with the key for Banshee though.  When using Update Manager it throws out the following error message:

```
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures were invalid: BADSIG 4874D3686E80C6B7 Launchpad PPA for Banshee Team
```
Any ideas?

---

### Post by waspbr on 2009-01-25
I had that too, all you have to do is input the key " manually" 

go to [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x4874D3686E80C6B7]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x4874D3686E80C6B7")
actually to make things easier I will just post the text here

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXWDEQEEAMoYQN5/6HptUWokWxGPNrJL8BtixSVpAjOMpNyzN27I6Ofl+5FWf+OidUpI
2brAq8uspnvCxdRU7nYNJjaEZU3lyS1R48SpeCXi4ynP5o4nOHv4wXnjTesszbimXLWfnOjN
G32rI+fMLuXderCU3ZMoHLqnhm/0o3JHVjwswkCLABEBAAG0HkxhdW5jaHBhZCBQUEEgZm9y
IEJhbnNoZWUgVGVhbYhGBBARAgAGBQJJeqdKAAoJEEF/tkJIIf4k20MAoISSdMjpHlPQgWmq
a+4hcuOhoCkFAJ9KabMOR6M/t9b1GidzRKvT+5IJx4i2BBMBAgAgBQJJdYMRAhsDBgsJCAcD
AgQVAggDBBYCAwECHgECF4AACgkQSHTTaG6AxrcH8gP/XXQHv1WTXfRSXvd4xykkLy+BEIZz
ImdTM8qyAoLtMsZFOKPEer1yfdB59AQXxnpm541YEn2hUmGhUgzz0XyTg+HCXQs8Go1AC4ie
7Mdl1uMnD144T6x+G/VVojXpJ4RswNS3r6ZVoVTxQm75EBoYqOwOByzh4oq1vE5VL6dNoqE=
=dWkD
-----END PGP PUBLIC KEY BLOCK-----

```

then copy the text. 

go to gedit (text editor) and paste it. I saved the file as banshee.asc, do the same on your desktop or home folder  (your call)

then go to software sources (System>Admin>Soft. Sources), and at the Authentication tab, click on the " Import Key File" button, select the file you have just saved. close the software sources GUI and refresh (sudo apt-get update)

---

### Post by Merkaba_ZA on 2009-01-25
Thanks waspbr.  I followed your instructions, but I'm still getting the BADSIG error.  I've resorted to installing Banshee via the deb file for the time being.

---

### Post by bruce89 on 2009-01-25
Wouldn't it be better if the script used wget, as it's installed already?

---

### Post by blackgr on 2009-01-25
well i use curl in general as it  prints page by default to the output. It can be also done with wget but i found it easier with curl

---

### Post by mjwood0 on 2009-01-25
Script worked great!  Thanks!

---

### Post by loomsen on 2009-01-26
Script worked for me after some slight modifications.

1.) At first it stopped after the sudo apt-get install curl part cause curl was already installed on my system.
So I commented this part out.

2.) I have my custom repo sources in a file in 
**/etc/apt/sources.list.d/custom.list**
so I had to change the path from /etc/apt/sources.list accordingly.


Thanks.

---

### Post by inspired on 2009-01-26
> **blackgr said:**
> I made this small bash script. it will check you intrepid system for all launchpad sources and will download and install the keys for you!

Who ever wants this for Hardy. Just edit the script and change intrepid to hardy

edit:
You have to run this with sudo

Thanks buddy... much appreciated.

---

### Post by psy-kami on 2009-01-26
Thanks alot for the script it worked great, although for some reason i still cant install the latest banshee, if any of you have any idea i would be very greatfull, it appears as an update but i get a messege telling me that i need to update alot of dependencies, and i have been looking for them, but it has shown to be pretty much impossible, thanks for the attention and in advance for the help!!!

---

### Post by psy-kami on 2009-01-26
> **psy-kami said:**
> Thanks alot for the script it worked great, although for some reason i still cant install the latest banshee, if any of you have any idea i would be very greatfull, it appears as an update but i get a messege telling me that i need to update alot of dependencies, and i have been looking for them, but it has shown to be pretty much impossible, thanks for the attention and in advance for the help!!!

Problem solved!!
It was a stupidity, I was using the apt sources.list entry for intrepid instead of hardy which is the one I was suppose to use!!!   :-P

---

### Post by jblackhall on 2009-01-27
There should really be an easier way to do this from Launchpad.  For example, they say:
> This repository is signed with  B9F2A424372C883C411D917F5AFADBD4AA1C92B0   OpenPGP key. Follow these instructions if you want to install packages from this PPA. 

Is there an easy way to just copy and paste that string somewhere in Import under Software Sources and have it work?  If not, there should be!

And for record, "Follow these instructions" link is not very helpful.  I was able to figure it out, but it's definitely more complicated than it needs to be!

---

### Post by travnewmatic on 2009-01-27
thank you!

---

### Post by mb_webguy on 2009-01-27
> **jblackhall said:**
> There should really be an easier way to do this from Launchpad.  For example, they say:


Is there an easy way to just copy and paste that string somewhere in Import under Software Sources and have it work?  If not, there should be!

And for record, "Follow these instructions" link is not very helpful.  I was able to figure it out, but it's definitely more complicated than it needs to be!

What you can do is click on the string, which will take you do a search results page.  On that page are two links.  Right click the first (under keyID) and save the link to your computer.  Now go to the Authentication tab in Software Sources, click the Import Key File button, and select the file you just downloaded to import the key.

And yes, it still seems like there should be an easier way to do this.

---

### Post by jblackhall on 2009-01-27
> **mb_webguy said:**
> What you can do is click on the string, which will take you do a search results page.  On that page are two links.  Right click the first (under keyID) and save the link to your computer.  Now go to the Authentication tab in Software Sources, click the Import Key File button, and select the file you just downloaded to import the key.

And yes, it still seems like there should be an easier way to do this.

Right, I figured out how to do it.  It should just be easier, given that they give you the string (which i assume is a fingerprint).  I submitted an idea on brainstorm to that effect: [http://brainstorm.ubuntu.com/idea/17692/](http://brainstorm.ubuntu.com/idea/17692/)

---

### Post by Johnny Utah on 2009-01-27
> **blackgr said:**
> I made this small bash script. it will check you intrepid system for all launchpad sources and will download and install the keys for you!

Who ever wants this for Hardy. Just edit the script and change intrepid to hardy

edit:
You have to run this with sudo

This is great, thank you!

Can I attach this on a post over at [http://www.kubuntuway.net](http://www.kubuntuway.net) ?  I'm sure others would love this. :D

---

### Post by blackgr on 2009-01-27
Sure! do what ever you like with it! change it if you want too.

---

### Post by martinjh99 on 2009-01-27
trying to get the key for this PPA:

```

#Screen configs
deb http://ppa.launchpad.net/kirkland/ubuntu hardy main
deb-src http://ppa.launchpad.net/kirkland/ubuntu hardy main

```

and the script runs fine - But doesn't seem to do anything...

```

martin@Willow ~ $ sudo ./launchpad-update
Reading package lists... Done
Building dependency tree
Reading state information... Done
curl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
cat: keyss: No such file or directory
rm: cannot remove `keyss': No such file or directory

```


Any problems?

Have installed said package from the PPA but want to get rid of the error on update.

---

### Post by blackgr on 2009-01-27
edit the script and change  "grep intrepid" to "grep hardy".Save it and execute it again

---

### Post by martinjh99 on 2009-01-27
That works thanks but i now get the following error...

```

martin@Willow ~ $ sudo ./launchpad-update
Reading package lists... Done
Building dependency tree
Reading state information... Done
curl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

curl: (77) error setting certificate verify locations:
  CAfile: /etc/ssl/certs/ca-certificates.crt
  CApath: none

curl: try 'curl --help' or 'curl --manual' for more information
martin@Willow ~ $


```

---

### Post by blackgr on 2009-01-27
do this. Search for ca-certificates.crt
```

sudo find / -name ca-certificates.crt
```

and post the output

---

### Post by martinjh99 on 2009-01-27
```

martin@Willow ~ $ sudo find / -name ca-certificates.crt
martin@Willow ~ $

```

---

### Post by blackgr on 2009-01-27
give me some time. Ill try to make a wget version of the program, with no curl

---

### Post by martinjh99 on 2009-01-27
Cheers - Thanks for the new script... :)

---

### Post by blackgr on 2009-01-27
Ok! Here comes the new wget version of the script! Just change the intrepid to hardy as you did with the first one and execute it! good luck

Edit: it will take some time to execute. Patience

---

### Post by martinjh99 on 2009-01-27
Still didn't work

```

martin@Willow ~ $ sudo ./launchpad-update2
martin@Willow ~ $

```

---

### Post by blackgr on 2009-01-27
Ok pal. Last try! Dont forget to change the intrepid part.

---

### Post by ninboy on 2009-01-27
Works flawlessly, thanks! In Intrepid x64

---

### Post by SadaraX on 2009-01-27
> **blackgr said:**
> I made this small bash script. it will check you intrepid system for all launchpad sources and will download and install the keys for you!

Who ever wants this for Hardy. Just edit the script and change intrepid to hardy

edit:
You have to run this with sudo

Your script works (shockingly) well. Good job man. Thanks.

---

### Post by White Barry on 2009-01-27
Too bad I can't *officially* thank you for this wonderful script but here it is in writing. Thank you so very much I was wondering about this for days... 

Didn't have to run it under sudo for some reason but hey it worked :p

---

### Post by yanick on 2009-01-28
Thanks, your script is great. but is "only for" intrepid. I did little mod, ubuntu code name is parameter now.

---

### Post by cutOff on 2009-01-28
w00t! Works fine. Many thanks for the nice script.

---

### Post by blackgr on 2009-01-29
Thanks yanick for the idea! Here is the final version of the script.

Changes:
-Scans all sources from /etc/apt
-menu to choose release name

---

### Post by terryandtaotao on 2009-01-29
Thanks blackgr for the script. I don't need to run my own command again once new source is added.

Great job!

---

### Post by rpete on 2009-01-30
> **mb_webguy said:**
> What you can do is click on the string, which will take you do a search results page.  On that page are two links.  Right click the first (under keyID) and save the link to your computer.  Now go to the Authentication tab in Software Sources, click the Import Key File button, and select the file you just downloaded to import the key.

And yes, it still seems like there should be an easier way to do this.

Hi, I have had two failures to configure due to missing pub keys.  I followed the instructions. I copied the script to a text file and saved it in the documents folder.  I went to Software sources, authentication tab and clicked import Key file but don't know how to select the file. All I can do is select the folder it is in, but I expected the script to then appear in the list under authentication and there is no change.   What should I do to complete this process?

---

### Post by blackgr on 2009-01-30
Just download the script and execute it with sudo.
example: 

sudo ./launchpad-update intrepid

---

### Post by smillerlsu on 2009-01-30
sweet... THANKS blackgr!

---

### Post by danpos on 2009-01-30
@Blackgr

A minor correction to your script:

* Original:

 wget -q --no-check-certificate `wget -q --no-check-certificate https://launchpad.net/~$i/+archive -O- | grep "http://keyserver.ubuntu.com:11371/pks/" | cut -d'"' -f2 ` -O- | grep "pub  " | cut -d'"' -f2 >> keyss

* Modified:

 wget -q --no-check-certificate `wget -q --no-check-certificate https://launchpad.net/~$i/+archive**/ppa** -O- | grep "http://keyserver.ubuntu.com:11371/pks/" | cut -d'"' -f2 ` -O- | grep "pub  " | cut -d'"' -f2 >> keyss

Only this way your script worked on my Ubuntu Hardy installation. ;)

JFYI. :)

Regards,

Danpos.

---

### Post by blackgr on 2009-01-30
> **danpos said:**
> @Blackgr

A minor correction to your script:

* Original:

 wget -q --no-check-certificate `wget -q --no-check-certificate https://launchpad.net/~$i/+archive -O- | grep "http://keyserver.ubuntu.com:11371/pks/" | cut -d'"' -f2 ` -O- | grep "pub  " | cut -d'"' -f2 >> keyss

* Modified:

 wget -q --no-check-certificate `wget -q --no-check-certificate https://launchpad.net/~$i/+archive**/ppa** -O- | grep "http://keyserver.ubuntu.com:11371/pks/" | cut -d'"' -f2 ` -O- | grep "pub  " | cut -d'"' -f2 >> keyss

Only this way your script worked on my Ubuntu Hardy installation. ;)

JFYI. :)

Regards,

Danpos.

:-O this is something i didnt notice! Thanx Danpos for the feedback :)

---

### Post by chamber on 2009-01-31
Worked like a charm

---

### Post by mad_max0204 on 2009-01-31
I got this working but now I have openoffice updates in update manager and I cant select them ...

Whats wrong ?


EDIT: Works now. Dont know why and dont know how but I just updated for 100th time and I can select all updates ...

---

### Post by GokuH12 on 2009-01-31
wOw! really good, thx! great idea with this script and good work of course :D

---

### Post by jbalaguer on 2009-02-01
Hey, works fine. Thx a lot.
Para hispano parlantes.
Descargarlo, descomprimirlo y abrir un terminal en la carpeta donde se hizo.
Luego escribir sudo ./launchpad-update intrepid (o hardy o jaunty, según proceda)
Esperar a que termine y ya está.
Fantástico trabajo. Gracias a todos.

---

### Post by rpete on 2009-02-01
> **blackgr said:**
> Just download the script and execute it with sudo.
example: 

sudo ./launchpad-update intrepid

Blackgr, thanks for the reply. I have hardy.  I tried substituting the command with hardy but it didn't work.  I notice a modification in the posts following for hardy and will use that.

---

### Post by rpete on 2009-02-01
> **danpos said:**
> @Blackgr

A minor correction to your script:

* Original:

 wget -q --no-check-certificate `wget -q --no-check-certificate https://launchpad.net/~$i/+archive -O- | grep "http://keyserver.ubuntu.com:11371/pks/" | cut -d'"' -f2 ` -O- | grep "pub  " | cut -d'"' -f2 >> keyss

* Modified:

 wget -q --no-check-certificate `wget -q --no-check-certificate https://launchpad.net/~$i/+archive**/ppa** -O- | grep "http://keyserver.ubuntu.com:11371/pks/" | cut -d'"' -f2 ` -O- | grep "pub  " | cut -d'"' -f2 >> keyss

Only this way your script worked on my Ubuntu Hardy installation. ;)

JFYI. :)

Regards,

Danpos.

You guys are way over my head in your grasp of Ubuntu. I also have hardy.  One problem I have with this great advice is I don't know the conventions for reading command lines.  In the above series I don't know if the replacement script should be typed exactly as written or if the quotation marks and arrows (>>) mean something else.

---

### Post by rpete on 2009-02-01
One more question, what does the straight vertical line mean in the script?  I don't have that on my keyboard. Does it separate commands? As you can see I am just a beginner so any help would be appreciated.

---

### Post by anirudhphadke on 2009-02-02
I came across this message, when I tried to update. I am not sure when and how this started, but need urgent help.

**********************************************************************

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/Ubuntu-Studio%208.10%20%5fIntrepid%20Ibex%5f%20-%20Release%20i386%20(20081028)_dists_intrepid_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

**********************************************************************

---

### Post by joanmunoz on 2009-02-02
Great, great job!! I had the same problem and after running the script it was solved. Thx!!

Joan

---

### Post by surfer57 on 2009-02-02
Thanks for the update....everything working fine now! :guitar:

---

### Post by SoulSmasher on 2009-02-02
splendid script, thanks!

---

### Post by stormtrooprdave on 2009-02-03
That script worked perfectly, thanks

---

### Post by studiomohawk on 2009-02-06
Thanks! I could've done it manually, but this is easier.

Could I have a permission to redistribute this script?
My native language is Japanese, and I have a blog about Ubuntu.
This is gonna save a lot of people in Japan.

Launchpad help is in English, It take time to translate, but with this script,
It is easier.

I am planning to redistribute it in my blog.

Thanks!

---

### Post by blackgr on 2009-02-06
The script is for you ppl :D. Do what ever you like with it! Im glad it helped you in the first place!

---

### Post by forger on 2009-02-07
I made a script as well, it fixes the ppa links and gets the gpg keys for launchpad ppas that are in /etc/apt/sources.list :)
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

### Post by studiomohawk on 2009-02-07
Thank you!
You are the Best.

And thank you too, forger.

---

### Post by manolomanolo on 2009-02-08
Please tag this thread as [SOLVED].

Also put the final version of the script in the first post: I just approached to this discussion and I've been trying all of the scripts instead of trying directly the last working version.

Thanks.
Nice job!

---

### Post by blackgr on 2009-02-08
Ok ppl! here is the final version.
-Auto detects ubuntu version
-Scans all repos and not just sources.list

To execute it Just do the following after you extract it

sudo ./launchpad-update

---

### Post by arashiko28 on 2009-02-08
> **blackgr said:**
> Ok! Here comes the new wget version of the script! Just change the intrepid to hardy as you did with the first one and execute it! good luck

Edit: it will take some time to execute. Patience

Thanks! It seem that solved my problem too!

---

### Post by geirha on 2009-02-16
With the help of awk and cutting some corners, I managed to make it a one-liner :)
```

awk -F/ '/^[[:blank:]]*deb[[:blank:]]+http:\/\/ppa\.launchpad\.net\// \
{print "https://launchpad.net/~"$4"/+archive"}' \
/etc/apt/sources.list{,.d/*.list} | \
xargs -- wget -q -O- | \
awk -F\" '/http:\/\/keyserver\.ubuntu\.com:11371/ {sub(/amp;op=index/,"op=get");print $2}' | \
xargs -- wget -q -O- | \
sudo apt-key add -

```

---

### Post by forger on 2009-02-16
1.3 version of my perl script, with http_proxy support :)
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

### Post by alka73 on 2009-02-19
Im downloaded the script an put it on my personal folder, I have this error in console:

[B]sudo ./launchpad-update intrepid
sudo: ./launchpad-update: command not found[/B]

Im new on Linux :(

My version: Ubuntu 8.10 intrepid

---

### Post by geirha on 2009-02-19
> **alka73 said:**
> Im downloaded the script an put it on my personal folder, I have this error in console:

[B]sudo ./launchpad-update intrepid
sudo: ./launchpad-update: command not found[/B]

Im new on Linux :(

My version: Ubuntu 8.10 intrepid

Locate the script in nautilus (the file browser), then drag the script into the terminal. The full path of the script will appear in the terminal. Add a space and "intrepid", and hit enter.

---

### Post by richrock on 2009-02-19
Works absolutely sweet in 8.10 - even after trying to do tutorials 'claiming' to have fixed this problem.  Will keep this script in my library just in case..  

btw - just run ```
sudo ./launchpad-update2
``` and it should run.  It may hang for around 10-20 secs, come up with confirmations ( I had 2 OK's) then exit.  You only need to make sure intrepid is mentioned in the source code of this script... and the one I dl'ded did.

To check it's worked, type ```
sudo apt-get update
``` and see if any errors continue to come up...

---

### Post by forger on 2009-02-20
[thread=1056099]**Update your Launchpad PPA repositories and apt keys**[/thread]

---

### Post by mmilliet on 2009-02-20
> **blackgr said:**
> Ok ppl! here is the final version.
-Auto detects ubuntu version
-Scans all repos and not just sources.list

To execute it Just do the following after you extract it

sudo ./launchpad-update

When I run the script, i get this message:

Release: hardy
Please Wait...
cat: keyss: No such file or directory
rm: cannot remove `keyss': No such file or directory

It appears keyss is not being created.

The message I get when i try to update is:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release: The following signatures were invalid: BADSIG F9FDA6BED73CDC22 Canonical Archive Automatic Signing Key <ftpmaster@canonical.com>


Mike M.

---

### Post by anirudhphadke on 2009-02-22
> **mmilliet said:**
> When I run the script, i get this message:

Release: hardy
Please Wait...
cat: keyss: No such file or directory
rm: cannot remove `keyss': No such file or directory

It appears keyss is not being created.

The message I get when i try to update is:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release: The following signatures were invalid: BADSIG F9FDA6BED73CDC22 Canonical Archive Automatic Signing Key <ftpmaster@canonical.com>


Mike M.
Same Error with me.

Release: intrepid
Please Wait...
cat: keyss: No such file or directory
rm: cannot remove `keyss': No such file or directory

---

### Post by tanchita on 2009-02-25
Help please!
I'm trying and trying and I can't do it!
I download script that says "launchpad-update-final.zip" and the one on the page 7 that says "launchpad-update.tar.gz" and both give me the same error

tanchi@Tanchi-laptop:~$ sudo ./launchpad-update intrepid
Release: intrepid
Please Wait...
cat: keyss: No existe el fichero ó directorio
rm: no se puede borrar «keyss»: No existe el fichero ó directorio
tanchi@Tanchi-laptop:~$ 

I looked on System, about Ubuntu and says that I have Ubuntu 8.10 so I don't understand why I can't do it

---

### Post by forger on 2009-02-26
tachita, try my perl script:
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

### Post by nhudan on 2009-03-06
> **blackgr said:**
> Thanks yanick for the idea! Here is the final version of the script.

Changes:
-Scans all sources from /etc/apt
-menu to choose release name

Thanks bro! it works for me!

---

### Post by b007patel on 2009-03-30
I have Hardy 8.04 and was getting this error. I followed the advice in this post, **_[a change to the script for Hardy]("http://ubuntuforums.org/showthread.php?p=6648252#post6648252")**_ , and made the following other change to the script:

changed:
[INDENT]for i in `cat fullsourceslist | grep "deb http" | **grep ppa.launchpad |** grep $RELEASE | cut -d/ -f4`; do
[/INDENT]
to:
[INDENT]for i in `cat fullsourceslist | grep "deb http" | grep $RELEASE | cut -d/ -f4`; do

<Note: removed **grep ppa.launchpad |** command from original **for** statement>
[/INDENT]
I think this should also help any users who get the

[INDENT]cat: keyss: No such file or directory
rm: cannot remove `keyss': No such file or directory
[/INDENT]
messages, regardless of Ubuntu distribution (i.e., whether you're running hardy, intrepid, jaunty, ...)

I guess mmillet just followed the manual steps outlined in Forger's original post **_[Update your Launchpad PPA repositories and apt keys]("http://ubuntuforums.org/showthread.php?t=1056099")**_ to get things working. Please note I **DID NOT** receive the second error in mmillet's post about signature verification/GPG.

Anyway, I hope this helps someone out there. It worked for me! :)

> **mmilliet said:**
> When I run the script, i get this message:

Release: hardy
Please Wait...
cat: keyss: No such file or directory
rm: cannot remove `keyss': No such file or directory

It appears keyss is not being created.

The message I get when i try to update is:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release: The following signatures were invalid: BADSIG F9FDA6BED73CDC22 Canonical Archive Automatic Signing Key <ftpmaster@canonical.com>


Mike M.

---

### Post by yug23 on 2009-03-31
thanks to blackgr, yanick and forger for making this a whole lot easier!!:D

---

### Post by Paul Vega on 2009-04-03
Hello

I have tried to run your script in Terminal. The terminal dissapears and I am left wondering what happened. I am still getting the Bad Sig errors. Am I doing something wrong?

---

### Post by har02052 on 2009-04-03
I got one of the earlier versions to work but as soon as it got changed to check all sources when I put it into the terminal it closes out the terminal.  Any ideas?  I have two sources which give me the no_pub key error and was hoping this would work to add those keys.  Any help?

---

### Post by b007patel on 2009-04-05
Hmmmm....

What you can do if running the script is closing the terminal is pipe the output (STDOUT and STDERR) to a file. So instead of running
[INDENT]sudo ./launchpad-update hardy[/INDENT]
run
[INDENT]sudo ./launchpad-update hardy > ~/scriptoutput.txt 2>&1 [/INDENT]

where "hardy" can also be "intrepid" or "jaunty" or whatever version of Ubuntu you're running.

If that output still doesn't help (i.e., what's in ~/scriptout.txt), post it on the forums, and we'll see what we can do.

Thanks,
B

---

### Post by cepal on 2009-04-10
Amazing... ! Ihave no idea why this is the only thing which got through the https proxy (localhost's squid)... Why do we need some over complicated perl scripts when this one-liner just does it all?

> **geirha said:**
> With the help of awk and cutting some corners, I managed to make it a one-liner :)
```

awk -F/ '/^[[:blank:]]*deb[[:blank:]]+http:\/\/ppa\.launchpad\.net\// \
{print "https://launchpad.net/~"$4"/+archive"}' \
/etc/apt/sources.list{,.d/*.list} | \
xargs -- wget -q -O- | \
awk -F\" '/http:\/\/keyserver\.ubuntu\.com:11371/ {sub(/amp;op=index/,"op=get");print $2}' | \
xargs -- wget -q -O- | \
sudo apt-key add -

```

---

### Post by ubuntubrian on 2009-05-06
Worked great! Many thanks:popcorn:

---

### Post by Keithhed on 2009-05-17
Thanks for the post, it worked for me :)

---

### Post by datakid on 2009-06-02
geirha's one-liner worked for me too - where other answers hadn't.

cheers!

---

### Post by n00bz on 2009-10-05
i am competently lost here. i'm haveing several problems with ubuntu, ummm i'm trying to get my wireless network card to work and apperently i need to update. i'm not sure if i'm at the right thread (if i'm wrong please provide a link to the correct thread) 

```
 W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://ca.archive.ubuntu.com jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://ppa.launchpad.net jaunty Release: The following signatures were invalid: BADSIG 3B22AB97AF1CDFA9 Launchpad PPA for Ubuntu-X

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/Release  

W: Failed to fetch http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/jaunty/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
```

thats my error messege, i have NFC about anything....please help

---

### Post by crivicris on 2009-11-30
I have just found this script and if it works for me I'll be really happy I was tired to go one by one. Thnak you a lot for your job.

---

### Post by swajime on 2009-12-30
> **blackgr said:**
> I made this small bash script. it will check you intrepid system for all launchpad sources and will download and install the keys for you!

Who ever wants this for Hardy. Just edit the script and change intrepid to hardy

edit:
You have to run this with sudo
**Many Thanks !** :)
The curl command would not work for me without the -L option.
I made some other changes just to fit my personal OCD-taste:
```
#!/bin/bash
#sudo aptitude install curl
LIST_FILES=$(ls /etc/apt/sources.{list,list.d/*.list})
LIST=$(cat $LIST_FILES |
   grep '^deb .*ppa\.launchpad.*karmic' |
   cut -d/ -f4)
for i in $LIST; do 
   KEY_PAGE=$(curl -sL https://launchpad.net/~$i/+archive |
      grep 'http://keyserver.ubuntu.com:11371/pks/' |
      cut -d'"' -f2)
   KEYSS=$(curl -sL "$KEY_PAGE"|grep '^pub  ' |
      cut -d'"' -f2)
   for j in "$KEYSS"; do
      curl -sL "http://keyserver.ubuntu.com:11371$j" | 
         sed -ne '/BEGIN/,/END/p' |
         apt-key add -
   done
done

```
Now if I could just fix "W: GPG error: [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) karmic-dell-mini Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9FDA6BED73CDC22", I'd be really really pleased!

j

---

### Post by nukitron on 2010-02-25
Thanks!!

---

### Post by cepal on 2010-02-25
Unfortunately, this script would not work if one has a little hacked repos and for some is using ifferent distro, like, in my case, I must use "jaunty" for "synapse", which didn't get a release for Karmic yet:
```

root@czchown0009352:/etc/apt/sources.list.d# grep jaunty *
synapse-ppa.list:deb http://ppa.launchpad.net/firerabbit/ppa/ubuntu jaunty main

```I would recommend to strip the "karmic" part out of the regexp. Also, soon, in April after there is a new ubuntu released (10.4), one would need to rewrite the script, so if you want to only process your current release repos, you should anyway use a variable provided by system, not a fixed string.

CePal

> **swajime said:**
> **Many Thanks !** :)
The curl command would not work for me without the -L option.
I made some other changes just to fit my personal OCD-taste:
```
#!/bin/bash
#sudo aptitude install curl
LIST_FILES=$(ls /etc/apt/sources.{list,list.d/*.list})
LIST=$(cat $LIST_FILES |
   grep '^deb .*ppa\.launchpad.*karmic' |
   cut -d/ -f4)
for i in $LIST; do 
   KEY_PAGE=$(curl -sL https://launchpad.net/~$i/+archive |
      grep 'http://keyserver.ubuntu.com:11371/pks/' |
      cut -d'"' -f2)
   KEYSS=$(curl -sL "$KEY_PAGE"|grep '^pub  ' |
      cut -d'"' -f2)
   for j in "$KEYSS"; do
      curl -sL "http://keyserver.ubuntu.com:11371$j" | 
         sed -ne '/BEGIN/,/END/p' |
         apt-key add -
   done
done

```Now if I could just fix "W: GPG error: [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) karmic-dell-mini Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9FDA6BED73CDC22", I'd be really really pleased!

j

---

### Post by HX_unbanned on 2010-04-03
Is there update for Karmic Koala or maybe even Lucid Lynx ???

Thanks. Much appreciated!

Respect to scripters!

---

### Post by geirha on 2010-04-03
> **HX_unbanned said:**
> Is there update for Karmic Koala or maybe even Lucid Lynx ???

Thanks. Much appreciated!

Respect to scripters!

No need in Karmic and Lucid, it automatically downloads the keys when you add the repository.

```
sudo add-apt-repository ppa:reposname/ppa
```

---

### Post by Asahi on 2010-06-09
> **waspbr said:**
> I had that too, all you have to do is input the key " manually" 

go to [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x4874D3686E80C6B7](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x4874D3686E80C6B7)
actually to make things easier I will just post the text here

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXWDEQEEAMoYQN5/6HptUWokWxGPNrJL8BtixSVpAjOMpNyzN27I6Ofl+5FWf+OidUpI
2brAq8uspnvCxdRU7nYNJjaEZU3lyS1R48SpeCXi4ynP5o4nOHv4wXnjTesszbimXLWfnOjN
G32rI+fMLuXderCU3ZMoHLqnhm/0o3JHVjwswkCLABEBAAG0HkxhdW5jaHBhZCBQUEEgZm9y
IEJhbnNoZWUgVGVhbYhGBBARAgAGBQJJeqdKAAoJEEF/tkJIIf4k20MAoISSdMjpHlPQgWmq
a+4hcuOhoCkFAJ9KabMOR6M/t9b1GidzRKvT+5IJx4i2BBMBAgAgBQJJdYMRAhsDBgsJCAcD
AgQVAggDBBYCAwECHgECF4AACgkQSHTTaG6AxrcH8gP/XXQHv1WTXfRSXvd4xykkLy+BEIZz
ImdTM8qyAoLtMsZFOKPEer1yfdB59AQXxnpm541YEn2hUmGhUgzz0XyTg+HCXQs8Go1AC4ie
7Mdl1uMnD144T6x+G/VVojXpJ4RswNS3r6ZVoVTxQm75EBoYqOwOByzh4oq1vE5VL6dNoqE=
=dWkD
-----END PGP PUBLIC KEY BLOCK-----

```then copy the text. 

go to gedit (text editor) and paste it. I saved the file as banshee.asc, do the same on your desktop or home folder  (your call)

then go to software sources (System>Admin>Soft. Sources), and at the Authentication tab, click on the " Import Key File" button, select the file you have just saved. close the software sources GUI and refresh (sudo apt-get update)
Confirm. thanks a lot!

You've save my day. :guitar:

---

### Post by jang12 on 2010-08-08
thanks all.

---

### Post by dutchman77 on 2010-08-23
Just my 2 cents...

I've only added Karmic and Lucid to the selection screen. For me is working fine!

Thanks!

---

### Post by rupertm on 2012-08-16
> **blackgr said:**
> Ok ppl! here is the final version.
-Auto detects ubuntu version
-Scans all repos and not just sources.list

To execute it Just do the following after you extract it

sudo ./launchpad-update

What am I doing wrong?

```
me@myhost:/tmp$ sudo ./launchpad-update
Release: precise
Please Wait...
cat: keyss: No such file or directory
rm: cannot remove `keyss': No such file or directory

```

---

### Post by my real name is steve on 2012-12-01
> **blackgr said:**
> Ok ppl! here is the final version.
-Auto detects ubuntu version
-Scans all repos and not just sources.list

To execute it Just do the following after you extract it

sudo ./launchpad-update

I've tried putting in /bin /opt /tmp /etc and several other places and executing it each time, but no dice when I try the sudo /.launchpad-update cmd in Terminal.
 
I'm at the limits of my Linux knowledge at this point.

can anyone tell me the specific path to put file in ?

I'm a bit lost.

thank you!

---

### Post by howefield on 2012-12-02
Old thread closed.

Feel free to start a fresh one.

---

