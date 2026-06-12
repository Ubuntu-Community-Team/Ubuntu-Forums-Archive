---
title: "No internet connection after &quot;online update&quot;"
date: 2009-04-14
forum: General Help
---

### Post by Ironhide on 2009-04-14
[B][SIZE="3"]Hello... I have a situation!
I'm learning with Ubuntu for the first time and I have to say that I just install Ubuntu 8.10 into my Acer Netbook by USB and it boot up just fine, and it looks and work awesome my friends. I was surfing the internet with firefox and everyting was fine. But I recive the messege of new updates available to download so I decided to download them. there was like around 270 files or updates available. When the updates finished downloading it ask me to restar firefox cause i think that one of the updates available was firefox and when I restarted firefox, it doesn't connects now to the internet. I have no connection to internet. Please help!!! Thanks![/SIZE][/B]

---

### Post by codeseer on 2009-04-14
Do you have a network status icon in the panel? Have you tried restarting? You should restart after that initial update.

How do you connect? Through an Ethernet cable or wireless?

When you type 'ifconfig' in the terminal, what do you get? What about 'ping google.com'? 'ping 209.85.171.100'?

---

### Post by Ironhide on 2009-04-14
[SIZE="3"][B]Yes there is a network status icon in the panel and I click on it and it says Not connected and I did restart my Netbook after that initial update and nothing. Im about to get a wireless router in a few days but right now I'm connecting through Ethernet

Please explain...[/B][/SIZE]
> When you type 'ifconfig' in the terminal, what do you get? What about 'ping google.com'? 'ping 209.85.171.100'? 

---

### Post by codeseer on 2009-04-14
The terminal can be found by clicking on 'Applications' in the upper-right corner of your screen, extending the 'Accessories' menu and clicking on 'Terminal'. I recommend creating a shortcut to this by dragging and dropping it on your desktop for quick access.

Type the following at the prompt and hit the Enter key:

```

ifconfig

```

Then type:

```

ping -c 1 google.com

```

and

```

ping -c 1 209.85.171.100

```

---

### Post by Ironhide on 2009-04-14
[SIZE="3"][B]Great!!!
Im at work right now, but when a get a chance
I'll try that my friend. Thanks for the great 
assistance. I'll let you know what happened![/B][/SIZE]

---

### Post by RandomNY on 2009-04-15
I'm having the same problem. I'm showing that I'm connected either with Wireless or wired ethernet connections but when I open up Firefox no webpages will show. It says there is no internet connection. I'm behind a Dlink router, pinging any ip doesn't work. 

This happend after I downloaded the updates and installed other programs through the package manager. 

I'm dual-booting Vista and ubuntu 8.10 on an Asus M50sa laptop.

---

### Post by Ironhide on 2009-04-15
[B][SIZE="3"]Ok... so I turned on my netbook and clicked on Firefox to see if there was any connection wish there was. So now I have connection again. Thanks again for your help codeseer. Hope it got fixed for you as well RandomNY.

You guys will see me around cause I've got so many thing to ask and doubts.
Take care!
[/SIZE][/B]

---

### Post by codeseer on 2009-04-15
> **RandomNY said:**
> I'm having the same problem. I'm showing that I'm connected either with Wireless or wired ethernet connections but when I open up Firefox no webpages will show. It says there is no internet connection. I'm behind a Dlink router, pinging any ip doesn't work. 

This happend after I downloaded the updates and installed other programs through the package manager. 

I'm dual-booting Vista and ubuntu 8.10 on an Asus M50sa laptop.

What does 'ifconfig' and 'netstat -nr' give you?

Can you connect to the router interface? Can you ping other systems on your local network, using their internal IP?

---

