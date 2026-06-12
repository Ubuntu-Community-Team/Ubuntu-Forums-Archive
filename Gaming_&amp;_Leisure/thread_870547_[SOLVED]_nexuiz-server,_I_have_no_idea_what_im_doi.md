---
title: "[SOLVED] nexuiz-server, I have no idea what im doing"
date: 2008-07-25
forum: Gaming &amp; Leisure
---

### Post by Potatoj316 on 2008-07-25
I want to set up a dedicated nexuiz server on my computer running ubuntu server 8.04.1.  I installed the nexuiz-server package but dont know what to do now.  What I read about installing nexuiz server on linux told me to download a package from the nexuiz website and put some files in ~/.nexuiz.  I dont have that directory because I dont have nexuiz installed on my computer.  I dont want to install nexuiz on my computer because I need to install 74 other packages, including many x packages as well.  I dont want to install these packages because I have a server, not a desktop computer.  Do I not even have to mess with these files because I installed nexuiz-server or what do I have to do.

---

### Post by ad_267 on 2008-07-26
Can't you just run "nexuiz-server"?

---

### Post by nille on 2008-07-26
To copy those files to the directory mentioned, you might have to create it yourself:
```
mkdir ~/.nexuis
```

Unfortunately I have found little good documentation on Nexuis server setup, and I have no clue myself. But I wish you good luck!

---

### Post by Potatoj316 on 2008-07-29
> **ad_267 said:**
> Can't you just run "nexuiz-server"?

Yup, I can't believe I didnt think of that.  I use the terminal all the time.  Maybe I was thrown off by a tutorial I read.  So thank you

my new problem is that when I see my server on the nexuiz servers list it has a rather high ping time or 9999.  It also connects me to 192.168.1.3 when I try to connect.  I am able to play but am doubtint anyone else can connect because 192.168.1.3 in an internal IP address.  I have forworded the correct ports (i think) to my computer, and have poked a nice little hole for them in my firewall.

---

### Post by detrate on 2008-07-30
> **Potatoj316 said:**
> my new problem is that when I see my server on the nexuiz servers list it has a rather high ping time or 9999
This is bug (feature?) other players outside your network will not have that ping. I repeat **the ping is false**.  It's 0 for the first few seconds, then 9999.

> **Potatoj316 said:**
> I have forworded the correct ports (i think) to my computer, and have poked a nice little hole for them in my firewall.
The default Nexuiz port is 26000.

If you want to run a server on the outside network, you're going to need to do a bit more configuring.

**The documentation for Nexuiz servers** can be found in the Docs/server folder.  Here is a link to the [latest SVN server documentation](http://svn.icculus.org/nexuiz/trunk/Docs/server/).  Please note that this documentation may have more information than what your version currently supports and it's usually safer to read from your local Docs folder.

You should setup a server configuration file.  The default is 

['**server.cfg**' found in your **Docs/server** folder](http://svn.icculus.org/nexuiz/trunk/Docs/server/server.cfg?view=markup)

You can name these whatever you please and call it as such:

```
./nexuiz-server +exec my_config.cfg
```

[A searchable list of Nexuiz's cvars and cmds can be found here](http://www.nexuizninjaz.com/toolz/cvar/)

---

