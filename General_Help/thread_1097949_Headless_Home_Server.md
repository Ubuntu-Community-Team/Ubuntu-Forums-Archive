---
title: "Headless Home Server"
date: 2009-03-16
forum: General Help
---

### Post by cloudstrife_uk on 2009-03-16
I an currently using Ubuntu Desktop but am planning on using Ubuntu Server on my new (well 2nd hand PC) in a headless mode (so I can tuck it out of the way and keep power consumption down!)

This is what I need from the server:
[LIST]
[*]**Samba File Shares** (will setup these once Webmin is installed)
[*]**Music Sharing** - currently use Samba shares for Music which my Xbox Media Center seems happy with but is there a 'smarter' way of streaming music to Windows XP (using VLC) along with XBMC?
[*]**CD Ripping** - currently using Grip which I find works perfect (pop the CD in, files appear in the music share and CD pops out) but is there a ripper that will automatically rip and tag audio CDs to MP3 without a using any display?
[*]**BitTorrent** - what is the best torrent server for downloading Torrents on a headless server?! Currently use Transmission and the web display over my network.
[*]**Updates** - I currently login onto the server every now and then to apply the updates - is there some way of doing this automatically or somehow notify me through a web interface/by email that updates/system restart is needed?
[*]**Document Scanning** - Not something I use at present but would like to able to scan in documents using my HP All In One Printer which would allow me to shred and make some physical space in my spare room!! My idea is that I could somehow scan and it automatically saved it as a jpeg to a shared folder?!
[/LIST]

Thanks,
Cloud

---

### Post by perrti-y02 on 2009-03-16
Something worth looking into which I am experimenting on now is ssh. It lets you have a terminal window on your normal linux machine that is running on the headless server. I think that made sense but do ask if it didn't.

For the rest I can be of little use at present.

---

### Post by Dr Small on 2009-03-16
2.) Why not just stream with VLC from the command line on the headless server?

3.) Why don't you just rip the CDs on your computer and scp the files to the headless server, either individually, or as an archive?

4.) You can use whatever you like, and port the display to your monitor with ssh, but personally, if you want to make things easy, you can install rtorrent (Please see K.Mandla's guide on "[Howt: use rtorrent like a pro](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)")

5.) Generally, the best advice for applying updates, is to be there when it is happening. Things do go wrong, and setting up any type of automatic update that could potentially go wrong at some point is asking for trouble.

---

### Post by cloudstrife_uk on 2009-03-19
Thanks for the replies. Had a look at SSH which looks interesting, needs further messing around.

Might have a go with VLC, didn't know it can be run from the command line!! 

rtorrent looks perfect and even if I still use 'Desktop' to start off will prob still use rtorrent in future.

In the meantime I have come across [VortexBox]("http://vortexbox.org/about/") which seems to tick all my boxes apart from BitTorrent side but I guess it would be easy enough to setup rtorrent?! Oh the only down side is its not based on Ubuntu :-( Anything similar out there based on Ubuntu?!

Cloud

---

### Post by Sub101 on 2009-03-19
Over ssh with the -X trigger you can load any gui program from your server pc onto the monitor of the pc you are using ssh from. Might be useful to you.

---

### Post by MrWES on 2009-03-19
> **cloudstrife_uk said:**
> I an currently using Ubuntu Desktop but am planning on using Ubuntu Server on my new (well 2nd hand PC) in a headless mode (so I can tuck it out of the way and keep power consumption down!)

This is what I need from the server:
[LIST]
[*]**Samba File Shares** (will setup these once Webmin is installed)
[*]**Music Sharing** - currently use Samba shares for Music which my Xbox Media Center seems happy with but is there a 'smarter' way of streaming music to Windows XP (using VLC) along with XBMC?
[*]**CD Ripping** - currently using Grip which I find works perfect (pop the CD in, files appear in the music share and CD pops out) but is there a ripper that will automatically rip and tag audio CDs to MP3 without a using any display?
[*]**BitTorrent** - what is the best torrent server for downloading Torrents on a headless server?! Currently use Transmission and the web display over my network.
[*]**Updates** - I currently login onto the server every now and then to apply the updates - is there some way of doing this automatically or somehow notify me through a web interface/by email that updates/system restart is needed?
[*]**Document Scanning** - Not something I use at present but would like to able to scan in documents using my HP All In One Printer which would allow me to shred and make some physical space in my spare room!! My idea is that I could somehow scan and it automatically saved it as a jpeg to a shared folder?!
[/LIST]

Thanks,
Cloud

1.Samba: [https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")
 - that should get you going on Samba

2. Music Sharing: I run mt-daapd on my headless home server
[http://www.fireflymediaserver.org/]("http://www.fireflymediaserver.org/")
 - it will allow you to share your entire library over the network. For Ubuntu clients, Rhythmbox supports mt-daap shares, and for Windows, iTunes also supports it. Oh...it's in the repositories; mt-daapd

3. Torrents: I installed transmission [http://www.transmissionbt.com/]("http://www.transmissionbt.com/")
 - I run the transmission-daemon on my server. It has a web GUI, so I can manage my torrents from my laptop via the web. There are other torrent apps, like rtorrent, but I liked having the web GUI>

4. Updates: If your server is not broke, don't fix it. I wouldn't run updates unless there was a security breach you need to fix. I subscribe to [https://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce"), and that way I can monitor any security issues and update as needed. If you choose to run updates, you can either run a root cron job
```
sudo crontab -e
```
or utilize the /etc/cron.daily, weekly, etc. Cron jobs will email you the results when completed. Just make sure you have set the /etc/aliases to whatever user name you gave yourself
```
root: administrator
``` <--example and you'll get all root email forward to that user.

Additional security: Are you behind a router? If so, and you want the ability to login to your server from the outside world via ssh, you need to forward port 22 (default), or whatever port you decide to use. I use port 22, however if you do, I would recommend using DenyHosts [http://howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts]("http://howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts")
 -- it's in the Ubuntu repositories. 

Lastly, run your server by Shields Up! [https://www.grc.com/x/ne.dll?bh0bkyd2]("https://www.grc.com/x/ne.dll?bh0bkyd2")
You can get some idea on how secure you server is.

Hope that helps,
Bill

---

### Post by piratebill on 2009-03-19
you could always install ushare for video and audio streaming

---

### Post by cloudstrife_uk on 2009-03-20
Thanks again for all the replies!

Am going ahead with a Ubuntu Desktop install-

1) Samba - will just be using this now to share printer and Home folders.
2) Music Sharing - rather than using Samba shares will use either ushare or Fuppes - from what I can see they both do the same thing, does one have more advantages over the other? (I was surprised to find that even though UPNP is the way forward there is no UPNP players for Windows XP, ended up using XBMC for Windows which can connect to UPNP shares with playback plus its the same as my XBMC so its all familiar).
3) CD Ripping - I can't rip locally and copy securely as my Netbook don't have a CD Drive, will continue with Grip hence the need to keep Ubuntu Desktop.
4) BitTorrent - rtorrent looked good but am looking at using TorrentFlux as it gives a web display so I can keep an eye on my downloads plus there is a Firefox extension so I can start the downloads with a simple right click of the torrent link.
5) Updates - I like the idea of applying to the security announcements and agree that updates shouldn't be installed automatically in case of errors.
6) Document Scanning - will just log in physically to the server desktop which the scanner is attached to to scan in documents.

With installing LAMP am looking at creating a secure webpage to link to Webmin, TorrentFlux, CUPS, Fuppes (I think it has a web page?!). I have limited HTML knowledge so could easily create the page with the links but how do I make it secure and to include the Ubuntu RSS Feed ([http://www.ubuntu.com/rss.xml)??](http://www.ubuntu.com/rss.xml)??)

On a final thought how easy is it to bring X10 Home Automation into the mix? I use it at the mo on a couple of lamps (with a remote) but having PC control (pref with web based control) would make it even better!

Thanks again guys!!
Cloud

---

### Post by mortuk on 2009-03-20
I am looking at doing the same, do you not have any plans for backups?

---

### Post by aeiah on 2009-03-20
im gonna put a word in for deluge as a bittorrent client. it can run as a daemon and you can connect the GUI to the daemon locally, over the LAN or over the internet. it also has a web gui for when you arent on a pc you can install deluge on.

whilst web guis are nice, i like the fact that deluge can act like a normal bit torrent client even though the actual downloading is being done by a daemon that could be on another pc.

---

### Post by cloudstrife_uk on 2009-03-20
I will get around to backups once sorted possibly using an external USB Hard drive attached to the server (and when cash allows!).

Just off to have a look at Deluge now, how do you 'connect' the GUI over the LAN?!

Below is a screenshot of a central webpage for the server, ideally I would like to secure it somehow possibly having to login using the local user profiles?

[IMG]http://img.photobucket.com/albums/v218/oohmatron/serverpage-1.jpg[/IMG]

Thanks,
Cloud

---

