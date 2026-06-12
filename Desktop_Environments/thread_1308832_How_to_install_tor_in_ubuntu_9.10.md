---
title: "How to install tor in ubuntu 9.10"
date: 2009-10-31
forum: Desktop Environments
---

### Post by unixstd on 2009-10-31
I am a China user. There is a GFW in our network. When I search or access some websites outside,usually  the connection was reset by it.
I want to install a tor in my ubuntu ,but I cannot intall it in 9.10.
Ubuntu team should place tor in their respository!

GFW is the short term for The Great Firewall of China, which is part of Gold Shield Engineering launched by Chinese government. The purpose of GFW is to filter information which the government considers not proper to spread in China, including pornography, violent, and political sensitive information, in other words, it is built to &#8220;purify&#8221; the cyber world in China. 
 Inside GFW, people complains that many excellent and usefully websites are blocked. These sites might be blocked simply because they are hosted on shared servers and one of the other sites on this server contains sensitive information.

I think the hackers should do something useful, like attacking GFW to fall down!

---

### Post by bigj2632 on 2009-11-15
[http://www.torproject.org/docs/debian.html.en](http://www.torproject.org/docs/debian.html.en)

---

### Post by Fzang on 2009-11-15
If you cannot access the tor website, you can try go through a proxy server to bypass the censorship. 

Here is the tor website through the proxy hidemyass:

[http://tinyurl.com/yd2kd5m](http://tinyurl.com/yd2kd5m)

---

### Post by tiger2wander on 2009-12-19
Read this: [https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)

good luck!

---

### Post by tiger2wander on 2009-12-19
Read this: [https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)

good luck!

---

### Post by namluc on 2009-12-20
i'm in china too, and struggling with this, in the end, i downloaded the key and the binary from

/torproject.org/dists/karmic/main/binary-i386

by using a proxy. but now i have the key and the binary sat on my desktop, it is a gzip file. I can't get them to do anything useful. i've been trying to /.configure etc, but to no avail. ubuntu refuses to see the key, i've saved it in gedit and renamed it tor.asc, but to no avail. all help very much appreciated!

---

### Post by spinny on 2009-12-27
> **tiger2wander said:**
> Read this: [https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)

good luck!

I read the above directions and i did what it said, and here is the output from my terminal....

jim@ubuntubox:~$ sudo /etc/init.d/tor start
[sudo] password for jim: 
Raising maximum number of filedescriptors (ulimit -n) to 32768.
Starting tor daemon: tor...
done.
jim@ubuntubox:~$ sudo /etc/init.d/privoxy start
jim@ubuntubox:~$ netstat -a | grep 9050
tcp        0      0 localhost:9050          *:*                     LISTEN     
jim@ubuntubox:~$ 

So i have also installed torbutton in firefox, and when i press it it goes green but then gives me the following message...

The most recent Tor proxy test failed to use Tor.

So i did the test again and it still failed. So now what do i do?? This is getting really frustrating to get a program going that in my opinion should be part of firefox.

So here is what i am running...

ubuntu netbook remix 9.10
wireless connection to a linksys router (linux version un modified)

I humbly request some help as i am still pretty green with ubuntu.

thanks

jim

---

### Post by spinny on 2009-12-28
bump...please help.

pretty please?

---

### Post by bryanlee1981 on 2009-12-28
I am having the same issue.  I get the following output which i assume means that TOR is running as intended, but when i visit the check.torproject.org website it says that TOR is not running.  Any ideas?

```
bryan@bryan-laptop:~$ netstat -a | grep 9050
tcp        0      0 localhost:9050          *:*                     LISTEN    
```

---

### Post by shadowlands on 2009-12-28
I am dual booting and having trouble with both microsoft and ubuntu.  in mic it works but after i turn it off it will not work any more.> **spinny said:**
> I read the above directions and i did what it said, and here is the output from my terminal....

jim@ubuntubox:~$ sudo /etc/init.d/tor start
[sudo] password for jim: 
Raising maximum number of filedescriptors (ulimit -n) to 32768.
Starting tor daemon: tor...
done.
jim@ubuntubox:~$ sudo /etc/init.d/privoxy start
jim@ubuntubox:~$ netstat -a | grep 9050
tcp        0      0 localhost:9050          *:*                     LISTEN     
jim@ubuntubox:~$ 

So i have also installed torbutton in firefox, and when i press it it goes green but then gives me the following message...

The most recent Tor proxy test failed to use Tor.

So i did the test again and it still failed. So now what do i do?? This is getting really frustrating to get a program going that in my opinion should be part of firefox.

So here is what i am running...

ubuntu netbook remix 9.10
wireless connection to a linksys router (linux version un modified)

I humbly request some help as i am still pretty green with ubuntu.

thanks

jim

---

### Post by craftomaniac on 2009-12-29
Hello.

Did you restart Firefox after you installed torbutton? Tor + privoxy + torbutton seems to be working fine for me.

Could you try pinging Google through tor?
```
torify ping google.com
```

---

### Post by spinny on 2009-12-29
How do i ping google with firefox??? I guess you do not want that code run through the terminal, since i am not sure if that is ever running under tor, right?

Sorry for the confusion.

---

### Post by spinny on 2009-12-30
bump... please help

---

### Post by notliw on 2010-01-07
You can try to check the proxy setting.

Also, please note that China ISP might have blocked known tor relays. Try to add bridges.

Bridge relays (or "bridges" for short) are Tor relays that aren't listed
in the main directory. Since there is no complete public list of them,
even if your ISP is filtering connections to all the known Tor relays,
they probably won't be able to block all the bridges.

You can send email to[SIZE=2] [email]bridges@torproject.org[/email][/SIZE], with contents of "get bridges". The auto reply will tell you the bridges to be used.

---

### Post by Galdor on 2010-04-09
> **spinny said:**
> bump... please help

Did U edit Ur privoxy config?
type:
sudo gedit /etc/privoxy/config

In the section "forward"
U'll find the following text:

#      To chain Privoxy and Tor, both running on the same system,
#      you would use something like:
#
#        forward-socks5   /               127.0.0.1:9050 .

uncomment the last line by deleting the '#'
and save the file.
then do
sudo /etc/init.d/privoxy restart

if Ur tor has not been started allready, plz start it with
sudo /etc/init.d/tor start

this should help.
   O:)

---

