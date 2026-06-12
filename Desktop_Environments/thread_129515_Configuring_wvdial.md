---
title: "Configuring wvdial"
date: 2006-02-13
forum: Desktop Environments
---

### Post by Temis on 2006-02-13
Following the wiki instructions I hit ctrl-o to save the file. But then this poped up
at bottom:
 "File Name to write: /etc/wvdial.conf"
I have no idea what my next move is.
( I  googeld and read some threads but did not find an answer)

---

### Post by Temis on 2006-02-14
Please anybody any idea?

---

### Post by chettyk on 2006-02-14
You appear to be using the **nano** text editor to edit the wvdial.conf file. When you get  **"File Name to write: /etc/wvdial.conf"**, all you have to do is press the <Enter> key. That will write the changes you have made to the wvdial.conf file. Then, to exit the nano program, press Ctrl-X (hold down the Control key and press the 'X' key).

---

### Post by Temis on 2006-02-14
Thank you chettyk, you are absolutely right, I am using nano editor as per
the wiki(ubuntu) guide. I give it another try. I am new to linux so I have no clue
how nano editor works.

---

### Post by Temis on 2006-02-15
I managed to configure wvdial. When I enter sudo wvdial, it dials but a recoded message tells me to hang up and try again. where did I go wrong. I did enter the correct phone number.

---

### Post by Temis on 2006-02-22
As mentioned in the last post I configure wvdial. Now when I dial I can hear
a buzzing noise for a while, then a ring and a recording telling me to hang up.
Then the line goes dead. 
 Then this messages:
No carrier! Trying again.
Sending ATDT <phone number>
Waiting for carrier
ATDT <phone number>

Timed out while waiting. Trying again
sending <phone number>
waiting for carrier

Using external modem USR 56K Faxmodem
Internet connection with Accelerator.
Any idea anybody? Please.

---

### Post by Temis on 2006-02-23
It seems there is no answer to this problem. Well I am not ready for Linux yet.

---

### Post by CameronCalver on 2006-02-25
Hey i got a 28k external dial up modem and i dont have the slightest idea how to set up can some1 help me

---

### Post by hajk on 2006-02-25
Hey Temis, you should realize that the wiki is not an official manual for getting things done, but merely the past contributions of other users. Some of the advice offered may be quite old or not up-to-date anymore, as is the case with using wvdial to establish a dial-up connection in Ubuntu Breezy.

The simple way of establishing a dial-up connection in Breezy is to use the Gnome System --> Administration --> Networking menu  (at the top of the screen). When you open this menu (and give the sudo password), the ppp0 interface should be one of the interfaces presented to you, though not yet activated. There may also be an eth0 interface, deactivate it if necessary, since you are'nt using it.

Now, highlight the ppp0 interface, then hit the Properties button, and Enable the interface. You must provide the telephone number, the user ID and the password needed for the connection. There are a few more tabs: Modem and Options. In Modem, choose /dev/modem; and under Options select all three options.  

Next, hit OK and then activate the ppp0 interface. You should hear it dial, and establish the connection -- the default gateway should list as ppp0. If all this works, you can leave this menu by hitting OK. The beauty is that any configuration details in files like /etc/network/interfaces and in /etc/ppp/peers are handled by Gnome. 

Shutting down requires deactivating the ppp0 interface in the same menu. The next time you dial in again you would merely activate the ppp0 interface again, no need to enter all the configuration details anew.

Now, if the above does not work, then you have an entirely different problem: it may be that your ID information isn't right -- ask your internet provider. Or, the modem driver may not work properly -- you might consider compiling a newer version.

Finally, Linux requires a bit of effort at first, though not as much in Ubuntu as in other distributions. The reward is the feeling of satisfaction you get when you have solved a problem successfully. Good luck!

---

### Post by thomasp on 2006-02-27
[QUOTE=Temis]It seems there is no answer to this problem. Well I am not ready for Linux yet.[/QUOTE]
Hi Temis,

Don't give up so easily! A lot of what linux is about is digging in and solving problems yourself!

I just installed ubuntu, but have been using other versions of linux for 5+ years. I don't know much about wvdial (I've always used kppp, which is standard with kubuntu), but it seems I'm going to have to figure it out. If I make some headway, I'll let you know.

thomasp

---

### Post by thomasp on 2006-03-09
Hi everyone,

A short while ago, I posted a question here wrt setting up telephone modem dialup on ubuntu, and a similar question at my local LUG. Several people gave some helpful answers, but I still couldn't get dialup working. To be more precise, I could dialup, and authenticate, but the line would be dropped 20 or so seconds later, before I could even perform a successful ping. I was getting errors 16 and 17 from pppd.

I used wvdial and Gnome's System->Network->Dialup, but without any success. I did (major) changes to both of their configurations, and still couldn't come right.

Now I've been using (and loving!) Linux exclusively at home for several years, and with these things I've learned that persistence often pays off. I've also learned that the 'right' thing to do afterward is to share it. So if this helps you, great!

For the purposes of this exercise, lets assume the following:
* my service provider in ZA is MWEB ([www.mweb.co.za](www.mweb.co.za))
* my logon with mweb is "mwblah" (that's not really it...)
* my password is "SuperDupper" (that really isn't true!)
* my machine's hostname is "amd1"
So where you see these, you will need to alter them for your ISP and logon details.

Also, note that the system utility/program which does dialup connections is called pppd.

First, a few files to check. Most of these can be opened in a shell (command line box) with
"sudo gedit <filename>". Often, you will need the "sudo" in front as these are system or root files. Also note that many/most of these config files understand that a line starting with a '#' is a comment; basically, its ignored. So if I say "take xyz out", it means add a # in front. Don't delete it, you may need to go back to it later, in which case you probably will not remember the exact wording, and things go south from there on! Don't email me if you do this...

* /etc/resolv.conf
  Mine contains only one line:
  domain mweb.co.za
  I can't say for sure if this line is even needed, but you may aswell add your ISP's hostname in there (without the www)

* /etc/hosts
  My original (ubuntu install) hosts file contained a whole lot of lines much like this:
  fe00::0 ip6-localnet
  I can't recall if it had a loopback, but AFAIK this is important, so make sure yours has this:
  127.0.0.1 localhost.localdomain localhost amd1
  Note that the last word is my machine's hostname; put yours in instead. You can find the name in /etc/hostname. If your /etc/hosts is empty or non-existant, create it ("sudo gedit /etc/hostname) and add the name you want to it, and use it in /etc/hosts. Any name will do, "bob" is OK. But its useful if its a name that's relevant for you.

* /etc/hosts.allow
  Mine is empty (except for comments about what you may want to put there, how it works, etc)

* /etc/hosts.deny
  Mine is empty (except for comments about what you may want to put there, how it works, etc)

* /etc/inittab
  This is the startup script for your system, only one line in it is important here. Near the beginning, you should have something like this:
  # The default runlevel.
  id:5:initdefault:
  This means that the default runlevel is "5". Linux knows several runlevels. The two most commonly used are 3 and 5. 3 is a "full" system, excluding x.org or xwindows, ie none of the graphical, cool stuff. Runlevel 5 is runlevel 3, but with graphics. Now some linux distributions define several other runlevels (and distributions do seem to vary in this regard), two of which are often runlevels 2 and 4. They're much the same as 3 and 5, except they disable all networking! So if you can't get dialup working, and you're starting with runlevel 4, guess what!? So if the runlevel isn't 5, change it to 5. Just one caution: make sure you have x.org running on your machine before you do this! If you don't, when next you boot up, things may go crazy! If you change the runlevel, restart the machine now for this change to take effect, and then carry on from here down. Note however, that if you've installed ubuntu, you most likely don't need to do this.

* /etc/ppp/options
  My ubuntu had a stack of options defined in this file. I slowly turned them all off (put a # in front of each line that didn't already have one) until the only option left was "lock". This option is quite important; it allows the dialer (pppd) exclusive access to your modem, so that no other process/program can access it. Things can go wrong if this option isn't set.

* /etc/ppp/chap-secrets
* /etc/ppp/pap-secrets
  These two files contain your ISP username and password for authenticating, and should both contain much the same thing. This way, pppd chooses what type of authentication to do, and you don't have to worry about it.
  After trying some of the other dialup methods, I found that these files were full of all sorts of stuff. Probably the best thing to do is to remove these lines (by placing a # at the beginning of the line), and adding this at the end:
  mwblah * SuperDupper
  Except, of course, change to your username and password.

Now there are two last files left to configure, which may not currently exist on your machine, in which case you'll need to create them (using "sudo gedit <filename>"). These two should be named after you ISP's name, just to make them easier to remember. Mine are named "/etc/ppp/peers/chat-mweb" and "/etc/ppp/peers/mweb". Name yours in the most convenient way, but they must be in the "/etc/ppp/peers" directory.
* /etc/ppp/peers/ISP
  Mine has the following lines:
  ***************************************************************
  debug
  ttyS0 115200 crtscts
  connect '/usr/sbin/chat -v -f /etc/ppp/peers/chat-mweb'
  noauth
  defaultroute
  netmask 255.255.255.0
  usepeerdns
  user mwblah
  logfile /home/pppd-log
  idle 600
  ***************************************************************
  You need to change the line starting with "connect" to end in the file you've named "chat-ISP".
  You need to change the line starting with "user" to have your ISP username/logon name.
  The line "idle 600" is usefull, but you may want to delete it. It tells pppd to turn off the modem after there has been no data for 600 seconds, or 10 minutes. It protects you from high telephone costs if you accidentally leave your modem connected.
  If your ISP does require PAP or CHAP authentication (as opposed to just using PAP or CHAP), you may need to remove the line "noauth". Play with this if you still have problems.
  "ttyS0" tells pppd what COM port to use. This is com1. Com2 is ttyS1, and so on. Note that the tty is lowercase, and the S is uppercase... Note that "/dev/modem" or even just "modem" may work.
  If your ISP has instructed you to use a different netmask (unlikely), change the line starting with "netmask" to the value they give you.

* /etc/ppp/peers/chat-ISP
  Mine looks like this:
  ***************************************************************
  ABORT "NO CARRIER"
  ABORT "NO DIALTONE"
  ABORT "ERROR"
  ABORT "NO ANSWER"
  ABORT "BUSY"
  "" "at"
  OK "at&d0&c1"
  OK "atdt0312688800"
  SAY "Dial Complete"
  "name:" "mwblah"
  SAY "Username OK"
  "word:" "SuperDupper"
  SAY "Password OK"
  ***************************************************************
  Replace with your ISP username/logon and your password.
  You'll notice the section "atdt0312688800". That's the telephone number to dial. It needs "atdt" on the front, then the full number, including any area codes, etc, as needed. I can't say for sure if it will accept dial modifiers, eg "+", "-", or " ". I guess you should avoid these?
  "name" and "word" are contractions of "username" and "password", so when your ISP asks these, "mwblah" and "SuperDuper" are sent as replies. Some ISPs do this differently, they may (for example) replace "username" with "logon". If so, you'd need to change "name" to "ogon" (avoid searching for the first character on a new line, as returned by the ISP...).


OK, so now (hopefully!) all the configuration is done. You should be able to dialup with this simple shell command:
  sudo pppd call ISP
(replace ISP with the name you chose for /etc/ppp/peers/ISP)

Now, pppd runs as a background process, so after you press ENTER on the command above, nothing seems to happen! Until a few seconds later when you hear your modem start to dial! So if you want to see how its managing, type this shell command:
  tail -f /var/log/messages
This listens to messages from pppd (and the kernel, for that matter), and puts them on the screen. You should be able to see the modem dial and connect. Press CTRL-C to escape, when you've seen enough.

When it appears that the connection is successful, try something like:
  ping [www.google.com](www.google.com)
which should result in something like this (if dialup worked):
  64 bytes from [www.google.com](www.google.com) (196.2.63.110): icmp_seq=1 ttl=47 time=169 ms
  64 bytes from [www.google.com](www.google.com) (196.2.63.110): icmp_seq=2 ttl=47 time=269 ms
  64 bytes from [www.google.com](www.google.com) (196.2.63.110): icmp_seq=3 ttl=47 time=167 ms

If this is the case, you're connected! If not, you may have some adjustments, etc, to make. Re-read this and make sure everything is in order.

OK, so pppd is running in the background, so how do you hangup? There's several ways:
* turn the modem off (works, but not recomended),
* pull the phone plug out (may not work, not recomended),
* if you know the commands "ps" and "kill", send the pppd process a HUP,
* or, the easy way, type in this command:
  sudo kill -HUP `ps -C pppd -o pid=`
  NB NB NB: the "`" is not a "'"! The "`" is usually on the "~" key...

The last thing to do is put the dialup and hangup commands in some nice format, so that they're easy to use. I suggest you make two desktop icons/shortcuts, one for each, one labeled "Connect", the other "Disconnect". While making the shortcuts (usually right click, Create New, Link to application, or something along those lines...), place these commands in the "command line" respectively:
Connect:        sudo pppd call ISP
Disconnect:     sudo kill -HUP `ps -C pppd -o pid=`

I'll leave making desktop shortcuts as a "exercise for the user".

Well, I hope this short monologue has been of help.

[thomasp, March 2006]

---

