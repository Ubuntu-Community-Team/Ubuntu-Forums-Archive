---
title: "Howto Get Firefox 1.5.0.2"
date: 2006-04-14
forum: Desktop Environments
---

### Post by ESPOiG on 2006-04-14
this is how you get Firefox 1.5.0.2, for anyone who wants to know

1. first backup your bookmarks and any other items of interest you want to keep (which are in /.mozilla/firefox/ in ur home directory or Bookmarks>Manage Bookmarks>File>Export> in Firefox to backup your bookmarks) in backup i mean copy them somewhere else like a folder on your desktop

2. download the attachment

3. make sure in properties>permissions> it is set to execute

4. then run it, it should ask for root password

once installed u may have to change the icons ect manually and make sure it is set to default application to be opened for wateva by system>preferences>preferred applications and type firefox

then copy your bookmarks back into the folder they came from, although it will be a different name or just import them via to bookmarks manager

if it dont work, it dont work it was just a test to see if it would, it worked for me though so lets see how it goes

ESPOiG

ps. this is just a file with all the instruction put into one file from the wiki on how to do it via ubuntu, it just thought this may make it easier

---

### Post by joelito on 2006-04-14
I created a *.deb for breezy to install this version of firefox for anyone interested...

Can be downloaded here

Link Full of Ads.
[http://www.megaupload.com/?d=CDJWWBLN ](http://www.megaupload.com/?d=CDJWWBLN )

Without Ads.
[http://www.blaksaga.com/hosted/firefox-1.5.deb](http://www.blaksaga.com/hosted/firefox-1.5.deb)

@ESP0iG

Sorry if you fell i  might be hijacking your thread but I didn't considered apropiate to open a new one on the same issue

Oh and BTW, thanks blacksaga

Edit(04/16/06): added link to fixed version

---

### Post by ESPOiG on 2006-04-14
doesnt matter :D... i was just tryin to help neone that needed help installin the latest version

---

### Post by granny4linux on 2006-04-14
ESPOiG, thank you so much; worked like a charm and most helpful.

---

### Post by ronmarley1 on 2006-04-14
I just followed the WIKI at [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) and made changes to the version number where applicable and everything is great!

---

### Post by danish_demon on 2006-04-14
[QUOTE=ronmarley1]I just followed the WIKI at [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) and made changes to the version number where applicable and everything is great![/QUOTE]

me too, worked like a charm.

i first tried using FirefoxUpdater (the script written by somebody on this board), but it reported an error.

---

### Post by ESPOiG on 2006-04-15
the execuatble script i just posted was just that stuff on the wiki i just adjusted some of it and put it in one file to run :D... anyone can add the backup bookmarks etc, and if you do upload it to plz

ESPOiG

---

### Post by risp on 2006-04-15
Why not download, extract to /usr/lib/firefox, and then make a link to /usr/bin? If you want to upgrade then you can overwrite the folder, every plugin and stored data will exist after upgrade.

---

### Post by JuggyUK on 2006-04-15
[QUOTE=ESPOiG]this is how you get Firefox 1.5.0.2, for anyone who wants to know

1. first backup your bookmarks and any other items of interest you want to keep (which are in /.mozilla/firefox/ in ur home directory or Bookmarks>Manage Bookmarks>File>Export> in Firefox to backup your bookmarks) in backup i mean copy them somewhere else like a folder on your desktop

2. download the attachment

3. make sure in properties>permissions> it is set to execute

4. then run it, it should ask for root password

once installed u may have to change the icons ect manually and make sure it is set to default application to be opened for wateva by system>preferences>preferred applications and type firefox

then copy your bookmarks back into the folder they came from, although it will be a different name or just import them via to bookmarks manager

if it dont work, it dont work it was just a test to see if it would, it worked for me though so lets see how it goes

ESPOiG

ps. this is just a file with all the instruction put into one file from the wiki on how to do it via ubuntu, it just thought this may make it easier[/QUOTE]


Hello All

By installing the latest version of Firefox will it solve issues with Flash because I have tried a few methods and they have not worked. 

1. Installing the arts libs and changing FIREFOX_DSP="none" or FIREFOX_DSP="arts" in the mozilla-firefoxrc file.

2. I had alook at what some people did, I referred to Adept Package Manager and installed all the related swf packages and still no luck.

I had installed Firefox and Opera (has the same problems of firefox - cannot see flash) from Automatix. As you know the Firefox version 1.5.0.1 but it does not work when I look at some sites;

[http://www.adidas.com/campaigns/verticalsfootball/content/index.asp?entrypoint=campaigns/plus10/tunit/tunit.xml&strCountry_adidascom=uk&strBrand_adidascom=performance](http://www.adidas.com/campaigns/verticalsfootball/content/index.asp?entrypoint=campaigns/plus10/tunit/tunit.xml&strCountry_adidascom=uk&strBrand_adidascom=performance)



So if I used the above method will it work for someone like me who is using kubuntu 5.10 (its not AMD64, although I am running kubuntu 5.10 on a AMD64 processor)?

I would be grateful if anyone can provide some help, I'm still a newbie to kubuntu and only have been using it for a week and a bit. :-D 

Thanks
JuggyUK

---

### Post by justinjstark on 2006-04-16
[QUOTE=joelito]I created a *.deb for breezy to install this version of firefox for anyone interested...

Can be downloaded here

[http://www.megaupload.com/?d=C6RRQ3NT](http://www.megaupload.com/?d=C6RRQ3NT)

@ESP0iG

Sorry if you fell i  might be hijacking your thread but I didn't considered apropiate to open a new one on the same issue[/QUOTE]

Ummm...please give me permission to host that file.  Seeing alll of those ads made me 10% stupider.

---

### Post by joelito on 2006-04-16
Please delete this post... sorry.

---

### Post by joelito on 2006-04-16
@blaksaga: Sure do...

But then I'd be glad if you could host the latest package instead. It fixes the menu entry and the internal version number.

To load the firefox 1.5 from a terminal using this package the comand is firefox-1.5

and here's a copy of the script used to run firefox without interfering with the oficial build
```

#!/bin/bash

if [ -d ~/.firefox-1.5 ];then
	echo "Profile found, loading firefox"
else
	echo "No profile found, creating profile"
	mkdir ~/.firefox-1.5
fi

/usr/local/lib/firefox-1.5/firefox $@ -profile ~/.firefox-1.5

```

the megaupload file is here ( [http://www.megaupload.com/?d=CDJWWBLN](http://www.megaupload.com/?d=CDJWWBLN) ) sorry for the ads but I have no other place to upload it right now

---

### Post by justinjstark on 2006-04-16
[QUOTE=joelito]But then I'd be glad if you could host the latest package instead. It fixes the menu entry and the internal version number.[/QUOTE]

Okay,

[http://www.blaksaga.com/hosted/firefox-1.5.deb](http://www.blaksaga.com/hosted/firefox-1.5.deb)

Thanks for making the .deb and please pass it around.  I'm sure other people would find this useful also.  :)

---

### Post by ESPOiG on 2006-04-16
[QUOTE=blaksaga]Ummm...please give me permission to host that file.  Seeing alll of those ads made me 10% stupider.[/QUOTE]

yeh give him permission all those ads suck on that site and all those upload sites... i just use my webspace that is provided from my ISP :P

---

### Post by beow on 2006-04-16
[QUOTE=risp]Why not download, extract to /usr/lib/firefox, and then make a link to /usr/bin? If you want to upgrade then you can overwrite the folder, every plugin and stored data will exist after upgrade.[/QUOTE]

Almost too simple I suppose... took me three minutes before I was up and running, and everythings works perfectly :p 

Maybee you should give some details for newbies although:

* Download the file from [http://www.mozilla.com/products/download.html?product=firefox-1.5.0.2&os=linux&lang=en-US](http://www.mozilla.com/products/download.html?product=firefox-1.5.0.2&os=linux&lang=en-US)

* Install

$ cd /usr/lib
$ sudo tar xvzf /home/user/Desktop/firefox-1.5.0.2.tar.gz
(if you are "user" and downloaded to "Desktop")

$ cd /usr/bin
$ sudo ln -s /usr/lib/firefox/firefox

That's it:)

---

### Post by joelito on 2006-04-16
beow: There's nothing wrong with that approach.

However I tend to believe that it's better to install any program that's not in the repositories in the cleanest way possible. That's what most other methods do.

---

### Post by justinjstark on 2006-04-16
Now, does anybody know how to get flash working with 1.5.0.2?  I tried getting the latest version directly from macromedia, followed their instructions, but it's still not working.  Any tips?

---

### Post by mishranurag on 2006-04-16
Will the update for firefox (1.5.0.2) come in repositories for Dapper? I just wanna sudo apt-get update

Anurag

---

### Post by Bil-E-daKid on 2006-04-16
Yeah - me too!

---

### Post by ESPOiG on 2006-04-17
[QUOTE=blaksaga]Now, does anybody know how to get flash working with 1.5.0.2?  I tried getting the latest version directly from macromedia, followed their instructions, but it's still not working.  Any tips?[/QUOTE]

did u try 'sudo apt-get install mozilla-flashplayer' ??

---

### Post by ESPOiG on 2006-04-17
i just uploaded the finished executable scripts for -

Installing Firefox 1.5.0.2 and
Installing Firefox Plugins to my website

[http://www.coregeek.net.tc/downloads/]("http://www.coregeek.net.tc/downloads/")

for the Plugins, you will have to edit it and remove the # for the plugins to work in Firefox 1.5.x, and make sure they are set to executable for them to run :D

i tried these both on a Fresh Install of Ubuntu 5.10 and they worked, so im happy

ESPOiG

---

### Post by beow on 2006-04-17
[QUOTE=joelito]beow: There's nothing wrong with that approach.

However I tend to believe that it's better to install any program that's not in the repositories in the cleanest way possible. That's what most other methods do.[/QUOTE]

I just wonder how much cleaner it can get than just un-taring to a directory? Personally I avoid un-official debs just because I don't know how they install, what they do etc, i.e. how "clean" they are.

---

### Post by ESPOiG on 2006-04-17
i like clean program installs to, but it does mean having to do it all properly and sometimes i cbf, so just doing it with a tarball works fine and becuase i use the program all the time it doesnt bother me, but wait till dapper is fiannly released and they should have the latest version supplied so we wont have to worry :D

---

### Post by Mr Egg on 2006-04-17
Hey everyone. ESPOiG, I tried installing Firefox using your executable text file first and it uninstalled my copy of Firefox, so then I wget the latest firefox and extracted it then ran the executable to download the .deb hosted by blaksaga and installed it and it worked fine. :)

---

### Post by ESPOiG on 2006-04-18
well mr egg... wat version did u have and what ubuntu version u using, cuz i tested it on Breezy with i think 1.0.6 or something :D and it doesnt unistall it it just does everything required to install the latest version from the ubuntu wiki that explains howto do it, it doesnt unistall anything but the totem plugin which doesnt work with 1.5.x and if you dont believe me look at it the commands in it and you will see it just redirects files and other stuff without removing the previous version :D

neone reading that may get confused :P... so very tired

ESPOiG

---

### Post by joelito on 2006-04-23
[quote=beow]I just wonder how much cleaner it can get than just un-taring to a directory? Personally I avoid un-official debs just because I don't know how they install, what they do etc, i.e. how "clean" they are.[/quote]

My Deb places firefox in /usr/local/firefox-1.5 and a script named firefox-1.5 in /usr/bin.

The firefox-1.5 scripts creates a profile in $HOME/firefox-1.5 so it won't interfere with the default install. I did this to keep the extensions on one version to conflict with the other.

---

