---
title: "Tinyproxy -- A must for many Ubuntu users"
date: 2006-01-26
forum: Desktop Environments
---

### Post by SuperMike on 2006-01-26
At my house, I'm a dad who uses Linux. I have some kids. They're starting to grow up and go to more questionable sites on the Internet (on urging from friends) and it's my job to police it. I am one of these dads who think that kids get enough exposure to bad stuff from TV, movies, and the public schools, and I don't think they need any more influences until their minds are mature enough to handle it. I also limit the kinds of movies they watch and the kinds of TV shows too. With my oldest child, I have let her watch a bit more than her younger brother, so I mean to say that I'm not the meanest dad in the world. I really do let a kid grow up -- I just try to wait until I think their minds are mature enough to wrap around certain concepts and strong enough to fend off peer pressure.

Anyway, I had to secure their Internet surfing. I needed to introduce a proxy. At my office, I spent a lot of time learning Squid proxy and it was frustrating but possible to get it going. That's when I discovered tinyproxy. With this, I was able to get going much, much faster. It's not as robust, but it's got just enough features to get you going.

Here's my cheat sheet on getting tinyproxy going at your home. Note that I recommend you stick with Squid if you plan on controlling more than 50 people with a proxy, and even at that, I recommend multiple network cards and/or multiple proxy servers behind a load balancer device for some real performance gains. But for average household use, tinyproxy is probably the tool for you.

1. From your home Linux system, type:

sudo gedit /etc/apt/sources.list &

2. Uncomment the universe options (temporarily) and save and quit editor.

3. Type:

sudo apt-get update

(WARNING: Ignore if Ubuntu pops open a window asking you to update your system -- if you update, you might end up pulling from the universe source and it could make your system more unstable. We'll undo this in a moment.)

sudo apt-get install tinyproxy
sudo gedit /etc/apt/sources.list &

4. Comment the universe options and save and quit the editor.

5. Type:

sudo apt-get update
sudo gedit /etc/tiny*/*.conf &

6. Uncomment these lines:

Filter "/etc/tinyproxy/filter"
FilterURLs On

7. Don't close your editor just yet. Think about your home subnet. Is it "192.168.0.x"? (In many cases this is the case if you are using Windows or are behind a Cable\DSL router. See what IP addresses your home PCs use and that should help you define your subnet. If you don't have a subnet, then that's beyond the discussion here about how to set up your own home subnet. Look elsewhere in Ubuntu Forums for that.)

8. In your tinyproxy.conf file that you're still editing, add a line like this for your current subnet, assuming it's "192.168.0.x":

Allow 192.168.0.0/24

9. The /24 stands for the "netmask". The short of it is that it allows 0-255 on the last part of the IP address, meaning, usually, your entire home subnet. I've got you going with a shortcut. If you want more help on netmasks, that's beyond the discussion here. I had to Google for it with keywords "squid and netmask" because tinyproxy and Squid use the same kind of "Allow" statement.

10. Now save your tinyproxy.conf file.

11. Type:

sudo cp /usr/share/tinyproxy/default.html /usr/share/tinyproxy/default.html.ORIGINAL
sudo gedit /usr/share/tinyproxy/default.html &

12. Now you see an HTML page. The reason I took you here is because this is the template page one sees when they have violated the proxy and gone somewhere they should not have. By default, this page is fairly ugly, and, frankly, confusing for young eyes to see. If you know a little HTML, edit this file to make it less confusing for children. Just note that this HTML is special in that it cannot load images -- it's just text you can put in here. Also watch out for the {} statements -- these are fillers that get filled in by the proxy. Now save the file when done.

13. Type:

sudo gedit /etc/tiny*/filter &

14. Now you're editing the filter file. In this part, it's actually pretty hillarious. I don't recommend you let anyone see you type this. You have to think up all the vile keywords on the planet that are not part of another word. For instance, if you look closely at the word "grapes", there's a vile word in there. The same with "advertisement" if you look close enough. So you can't filter on those kinds of vile words (that are inside "advertisement" and "grapes".) However, you can filter on other vile words. So, you can only use keywords that are not part of some other word. That discussion is beyond the discussion of this forum. And hey, if you don't have to type this vile list, but can find it on the Internet and download it, then that's your choice and will probably save you the hassle. You can also put in stuff like "http://www.dontgohere.com" for sites like "dontgohere.com" when you don't want users going there. When done, save the file.

15. Now we bounce the tinyproxy by doing:

sudo /etc/init.d/tinyproxy restart
sudo gedit /etc/crontab &

(Note it's a space after "tinyproxy" and before "restart".)

16. In crontab, add this line to bounce the tinyproxy at night so that you can kill any chance of a memory leak and make it run faster:

0 22    * * *   root    /etc/init.d/tinyproxy restart

Note that I did a <TAB KEY> after 22 and after the last * and after "root". Also, make certain there's a line wrap at the end of the line after "restart" or it probably won't "take". Note also I have a space between "tinyproxy" and "restart". Now save this file.

17. Now go to your kid's home PCs and change the settings in them so that they use this proxy. In my firefox, that's under a button in the Preferences dialog called "Connection Settings". Just point it to your IP address of the Linux proxy and set the port to 8888. I wouldn't bother with anything except HTTP proxy. Don't bother with SSL, FTP, all SOCKS, etc. Test this with yourself, first, of course, and see how it works. Note that your spouse might not like this proxy with amazon.com, ebay.com, or her banking sites, so you might want to put exceptions in the browser settings to not use the proxy when visiting these sites.

18. Note when you have to change your filter file, you have to restart the tinyproxy by doing:

sudo /etc/init.d/tinyproxy restart

19. When you want to debug what's going on, or simply to check up on your kids browsing habits, look in:

sudo /var/log/tinyproxy.log

20. Note that you can edit the log level to make it less verbose -- just read the info on that in your tinyproxy.conf file.

Enjoy!

---

### Post by ssalman on 2006-09-20
Thank you so much, your how to helped me a great deal in setting up my proxy/filter server. Do you know where I can find more filtering details to setup my rules? Thanks.

---

### Post by SuperMike on 2006-09-23
> **ssalman said:**
> Thank you so much, your how to helped me a great deal in setting up my proxy/filter server. Do you know where I can find more filtering details to setup my rules? Thanks.
Very good question. You can see the /etc/tinyproxy/tinyproxy.conf file has some notes inside, and you can 'man tinyproxy', but I'll admit that it's not very clear for newbies and I had to do some experimenting. I'd like to suggest you contact tinyproxy's most active maintainer...

   [email]rjkaes@users.sourceforge.net[/email]

...to ask where the preferred system op documentation is kept.

---

### Post by Ptero-4 on 2006-09-23
Hi. Does tinyproxy work on a computer that connects to the internet through dialup?

---

### Post by SuperMike on 2006-09-23
Dialup? Yes. It's a service (aka once called a "daemon" back in the olden days) and your browser points to it in the proxy settings on a certain TCP port number. It then checks the filter for authorized access and only permits out traffic that you have permitted.

Things also to note:

* There *might* be a way to see if someone knows how to change the option in Firefox's "about:config" URL such that you cannot override the proxy settings. Another route, although it takes some reading up on what a "chrome" is and how to design a tiny one in the "XUL" language, you can feed this XUL-based chrome file to firefox-bin, instead, and it will show a new kind of browser window with only the buttons and fields you want, thereby limiting one's access to edit the settings.

* I'm not 100% certain of this, but there *might* be a way in the tinyproxy or iptables firewall configuration such that it forces all network traffic on the system to not permit any network activity except that which travels through the proxy. I think I have heard of this before as an option somewhere. (Anyone else have any answer on this, guys?)

---

### Post by ssalman on 2006-09-26
Thanks SuperMike. But I have just hit a wall in my setup, I have a windows machine connected to tinyproxy which has an outlook email program, and I could not setup outlook to go through the proxy, I know it's not a linux question, but do anyone have a hint on connecting an email program through a proxy, I can replace outlook with whatever program I can get to work... googling turned out [SocksCap ]("http://www.socks.permeo.com/Download/SocksCapDownload/index.asp")but I couldn't get it to work yet!

Any help is appreciated.

Thanks.

---

### Post by SuperMike on 2006-10-05
> **ssalman said:**
> Thanks SuperMike. But I have just hit a wall in my setup, I have a windows machine connected to tinyproxy which has an outlook email program, and I could not setup outlook to go through the proxy, I know it's not a linux question, but do anyone have a hint on connecting an email program through a proxy, I can replace outlook with whatever program I can get to work... googling turned out [SocksCap ]("http://www.socks.permeo.com/Download/SocksCapDownload/index.asp")but I couldn't get it to work yet!


Set IE to use the proxy for all activity (not just web) and OE inherits the settings.

However, you won't get much benefit -- tinyproxy is designed to just look at URLs, not emails. If an email pulls from something remotely over HTTP/HTTPS, then yes, you may get some benefit.

A better approach would be to ensure you have SpamAssassin on your mail server and then switch to Mozilla Thunderbird. Then, turn on Junk Mail Controls in Thunderbird because it's turned off by default.

---

### Post by ssalman on 2006-10-06
Thanks SuperMike, I tryed to go that direction but it didn't work, I used the following [site]("http://www.proxyway.com/www/proxy-server-anonymous-public-faq.html#012") howto to setup a [SocksCap]("http://www.socks.permeo.com/Download/SocksCapDownload/index.asp") on the machine, but still was not able to get OE to work.

My goal is just to get emails and not to filter them, so I don't really need SpamAssassin or TinyProxy to filter the incoming messages, I just need to be able to connect to the SMTP and POP3 servers through the proxy machine as it is the only machine in the network with internet access... any ideas... Thanks!!:-D

---

### Post by peanut butter on 2006-10-07
can you access the internet (with a web browser) on your windows machine without the proxy configured?

if you can then i would suggest using an old machine as the proxy instead of your gateway also acting as a proxy.

---

### Post by ssalman on 2006-10-09
Okay, here is my setup...

Internet <===> Ubuntu Proxy PC <===> Wireless Router <===> Windows PCs

So you see, without a proxy there is no internet connection at the Windows PCs. But when using the proxy I can surf the internet from any of the windows PCs, the trick is how do I setup the SMPT/POP services so that it goes through the proxy too? knowing that Outlook Exchange (OE) probably does not have Proxy settings... and I tried to do the SocksCap thing and it didn't work for me...

Any ideas... thanks.

---

### Post by Hatrist on 2006-10-12
Hello!

I am having some problems with tinyproxy:
I've configured my second PC in the other room for the proxy and there's a perfect connection to the Internet. The problem is when I try to login in my Skype account - it just can't make a connection to the Skype server! I've already checked the settings and they seem fine:

HTTP proxy: 192.168.0.1
Port: 8888
/in IE/Firefox are the same/

Any help will be appreciated.

---

### Post by SuperMike on 2006-11-11
I suspect Skype doesn't work through this kind of proxy because it's a binary data stream with no HTTP headers. Tinyproxy is really only good for filtering web content on ports 80 and 443, and you might as well say port 80 because what site do you know has bad stuff on HTTPS? That's not to say you can't use this filter -- just don't set it for all ports, just HTTP traffic on port 80.

---

### Post by SuperMike on 2006-11-11
I don't believe tinyproxy works for SMTP/POP traffic -- just web traffic on ports 80 and 443.

---

### Post by kcallis on 2006-12-28
SuperMike,

You are not alone... I am the same type of father! I looked for the filters file to edit, but that did not exist... Should I remove and re-install tinyproxy in order to get the filters file?

---

### Post by anotherMichael on 2006-12-28
Just noticed this thread. 
As an improvement I recommend installing dansguardian instead of attempting to manually generate your filter list.  

Dansguardian scans the pages on the fly and comes with predefined filters that in my experience beat many commercial one.

For my home set up I've loosly followed  this guide [http://www.vollmar.ch/dansguardian-e.html](http://www.vollmar.ch/dansguardian-e.html). 

In the nutshell all you need is (I am sorry I write it from memory) 
1.
```
sudo apt-get install tinyproxy dansguardian 
```

2. edit dansguardian configuration as described in above guide 

in /etc/dansguardian/dansguardian.conf,
# Comment this line out once you have modified this file to suit your needs:
# UNCONFIGURED

and verify  the following 3 settings: 
      filterport = 8080 
      proxyip = 127.0.0.1
      proxyport = 3128 

3. save, restart dansguardian:
```
sudo /etc/init.d/dansguardian restart
```

4. Modify kids browser settings to use the IP address of your ubuntu computer as proxy address and port 8080 (you can use instructions provided above)

That it. Now test it ..  try to google for something offensive and click the result, you should get the Dansguardian blocked page instead. 

As the somewhat drastic improvement you may want to also use your internet router settings to completely block IP addresses of kids pc's from accessing internet. The actual  setting varies by the type of the router.  
In such setup blocked PCs will still be able to browse the web using proxy but attempts to bypass it or use unprotected applications like chat, internet games will not be possible. If you know the ports used by applications that you approve (e.g. specific game) you may be able to specify exceptions to filtering rule on your router.

---

### Post by SuperMike on 2006-12-28
> **kcallis said:**
> SuperMike,

You are not alone... I am the same type of father! I looked for the filters file to edit, but that did not exist... Should I remove and re-install tinyproxy in order to get the filters file?

Oh, did I not tell you? Sorry about that. You have to create this file yourself. Sorry I didn't get back to you sooner.

You do it like this. 

I can only get you started because this filter file is like the most vile thing on the Earth in that you have to think of everything disgusting, and get super-creative in a really sick way, and type it into this file so that it filters out the URLs. And some things you can't just type into the file because the word is inside another word. For instance, "r-pe" (you know what word I'm talking about) is inside "grape". So if you block that word, you also block most sites that deal with fine wines or grape juice! In that case, you have to get creative and start to think about how URLs look when you go to some of these bad sites.

For instance, I did an image search on Google for "p-rn" (you know the word I'm talking about :mrgreen: ) and it showed all kinds of sick and twisted pictures. I clicked on one and it showed an HTML page with images on it. I then clicked on an extraordinary image of a very healthy young lady and it expanded into 1024x768. \\:D/ Thank goodness my door was shut and locked to my home office. But then I looked at the URL and I noticed it ended with:

/01.jpg

So then I started thinking -- how many legitimate sites without p-rn do you know of that have image URLs that end with /01.jpg, /02.jpg, etc. Not many. And then I thought, well, it's worth it to get rid of any capability of visiting sites like that. So I threw something like this into my filter file:

/01.jpg
/02.jpg
/03.jpg
...and so on

Okay, so now that you know what content to put into the file, here's how it is composed. You do:

$ sudo touch /etc/tinyproxy/filter
$ sudo nano /etc/tinyproxy/filter

So here's something to get you started. At the top of my filter file it reads:

myspace.com
neopets.com
Evil
evil
userplane.com
euroclick.com
fastclick.net
casalemedia
.exe
erotic
reliaquote.com
/01.jpg
/02.jpg
amateur
...and so on on and on and not in any particular order

Note also that you can have a problem with a word like "a--" (donkey :---) ) because it's a part of other words, so you have to get creative. In order to block that word, I had to do something like the following, but substitute "x" with the word "a--":

-x-
-x/
/x-
/x/
/x-
/x+
/x=
/x%20
+x+
+x-
-x+
-x/
+x/

...and so on. It's rather painful, actually, to do all this, but oh well -- it works.

Now if I had an easier way to do this, I would, but unfortunately that's the way it is.

---

### Post by SuperMike on 2006-12-28
> **anotherMichael said:**
> 
As an improvement I recommend installing dansguardian instead of attempting to manually generate your filter list.  


All: I recommend you consider Dansguardian for yourself and make a decision on which way you prefer. For me, I got used to tinyproxy and I liked having the ability to add/remove entries from my filter file without much hassle. Since I have something that works, I didn't bother switching to Dansguardian.

---

### Post by ssalman on 2006-12-29
can we use regular expressions in the filter file?

---

### Post by SuperMike on 2006-12-29
I think so, ssalman. It's in the documentation somewhere for tinyproxy, I think I once saw a long time ago. I just don't know how, and even if I did know how, I wonder how I could be effective at getting everything I want in there -- regular expressions require a heck of a lot of thought for me and I muddle through them. However, if you ever come up with a great way to do much of what one wants with regex's, please share! :)

---

### Post by kcallis on 2007-01-03
SuperMike,

I just read your reply, and it was very informative, although I went a different route. I actually installed Danguardian which is doing all of the filtering. So far it is doing a great job of doing that, but I do have some issues. I need to look at getting several things working in order to impose to some slight control on my daughter's system.

Because I have vnc installed, I occassionally looks at what she is searching at any given time. Most of the time she is looking at her latest boyfriends (the singing group of the week). But I need to find someway to easily filter out searches for her boyfriends if I find that to be a distraction to her class work, etc.

The second issue is I need to get tinyproxy to work in conjunction with iptables, so that I can put a policy in place like the following:

M-F 7A-7P - Limited to searches through various edu sites and filter on non acceptable sites and any site/searches that I want to limit.

M-F 7P-10P - Proxy is in effect, but open searches and access.

M-F 10P-7A - Access to internet is off

F-Su - Proxy is in effect, but open searches and access.

Boy, working with teenagers is a lot of work!!! :)

---

### Post by SuperMike on 2007-01-03
kcallis,

I feel your pain. Okay, let's get to work.

I think I [**infer**]("http://www.vollmar.ch/dansguardian-e.html") that Dansguardian uses tinyproxy for the filtering. If so, then it's got a filter file kept as '/etc/tinyproxy/filter'.

Do you know how to edit '/etc/crontab' in the special way to put in Bash script schedules for things like you describe above?

The Bash scripts would be fairly simple:

* M-F 7A-7P - as root, swap out the '/etc/tinyproxy/filter' file with another and then do:

/etc/init.d/tinyproxy stop; /etc/init.d/tinyproxy start

* M-F 7P-10P - again, swap filter file, but this time it's got nothing in it

* M-F 10P-7A - block all Internet. No need for iptables changes -- just do:

/etc/init.d/networking stop

....and at 7A, do:

/etc/init.d/networking start

* If you want to build a quick and easy iptables firewall, anyway, and keep it running all the time, [**read this**]("http://www.ubuntuforums.org/showpost.php?p=1882492&postcount=1").

* F-Su - swap out filter file with an empty one

Here's an example of a sample Bash script, and you could stick it in /root/bin for instance.

#!/bin/bash
mv /etc/tinyproxy/filter /etc/tinyproxy/full_filter
cp /etc/tinyproxy/no_filter /etc/tinyproxy/filter
/etc/init.d/tinyproxy stop
/etc/init.d/tinyproxy start


Get it?

---

### Post by dannyboy79 on 2007-02-07
> **SuperMike said:**
>  3. Type:

sudo apt-get update

(WARNING: Ignore if Ubuntu pops open a window asking you to update your system -- **if you update, you might end up pulling from the universe source and it could make your system more unstable**. We'll undo this in a moment.)



I think you're providing inaccurate information here. The way apt-get or aptitude update works is that it only will "update" the index of packages available for your system using the repositories that you have in your sources.list which are not commented out. So I'll agree with you that the Universe Repo does have "some" untested programs in it but there is no way that they're just gonna install themselves which could then make your system unstable. What this will however do, is if a person is using synaptic, they uncomment the universe repo, then they hit update, their synaptic list of available programs will "update" and show NEW programs that they can install which again could lead to an unstable system. BUt I want to make it clear that simply uncommenting the universe or multiverse repos and hitting update, then when your system asks you if you want to update, yes, you should update, of course unless you're only intention is to simply install 1 program from that repo and then you're going to uncomment it again like your instance. According to man apt-get:
**update** update  is  used  to  resynchronize the package index files from
              their sources. The indexes of  available  packages  are  fetched
              from the location(s) specified in /etc/apt/sources.list. For exâ
              ample, when using a Debian archive, this command  retrieves  and
              scans  the  Packages.gz files, so that information about new and
              updated packages is available. An update should always  be  perâ
              formed  before  an upgrade or dist-upgrade. Please be aware that
              the overall progress meter will be incorrect as the size of  the
              package files cannot be known in advance.

and even if you uncommented the universe and wanted to do an upgrade, you can do this safely as well because it's only going to upgrade programs that were already installed when ubuntu was installed. per man apt-get.
**upgrade**
              upgrade  is  used to install the newest versions of all packages
              currently installed on the system from the sources enumerated in
              /etc/apt/sources.list.  Packages  currently  installed  with new
              versions available are retrieved and upgraded; under no  circumâ
              stances  are  currently  installed packages removed, or packages
              not already installed retrieved and installed. New  versions  of
              currently  installed  packages  that  cannot be upgraded without
              changing the install status of another package will be  left  at
              their current version. An update must be performed first so that
              apt-get knows that new versions of packages are available.

---

### Post by airtonix on 2007-05-01
**@ssalman:**[LIST=1]
[*]how many network cards are in your ubuntu proxy machine?
[*]I have two in mine.[LIST]
[*]one connects to a switch that my flatmate uses to hook up a computer. 
4 others can hook up at this switch too.(inside the house)
[*]the other goes to my adsl router.(the internet)[/LIST] 
[*]I run firestarter and bridge the two cards with the controls under preferences.[LIST]
[*] this allows them to access my ubuntu server (what you refer to as a proxy) an the internet
[*]i can use wondershaper to shape the total speed available to that switch down to dialup speed..lol...(i am the one paying for it all)[/LIST] [/LIST]**All :**[LIST]
[*] i like this setup, but i want to use a content-filterer for adverisments.
[*]i want it inline, ie interact with the network stream like wondershaper does.(iptables/chains etc whatever)
[*]i dont want to change the client browser settings.
[*]i'd prefer not to stuff with wondershaper[/LIST][B]Thoughts
[/B]I  could proly get round this by using vmware to run two virtual servers that are linked (network-wise) in series : 

switch => realMachine[ virtualServerOne(proxyFilter) => virtualServerTwo(wondershaper) ]

attached is my current setup.  I would run the two extra virtualmachines running some reall small linux distro...one is running a filtering-app and it is the gateway for the 10.1.1.1 NIC device, its gateway is the wondershaper virtualmachine whose gateway in turn is the 192.168.0.10 NIC device...

...gah proly doesnt make sense....but there...i spewed it out.

what you guys think?

---

