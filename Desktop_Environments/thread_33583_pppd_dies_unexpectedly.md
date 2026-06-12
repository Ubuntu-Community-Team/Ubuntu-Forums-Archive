---
title: "pppd dies unexpectedly"
date: 2005-05-11
forum: Desktop Environments
---

### Post by kevanf1 on 2005-05-11
I have just tried to set up a dial in connection with Kubuntu.  To cut things short all the hardware is fine and set up.  The connection dials out but for some reason I get the error message stating pppd died unexpectedly.  I have checked the log file and it seems to indicate that my password is not being authenticated.  The same PC works ok with a SuSE disk and indeed my Ubuntu disk (separate removable drives).  There is nothing wrong with my internet account as I have checked that on another PC (hence being able to post this message).  Authentication is pap/chap and all timeouts are at the full amount.  I have gone back and double checked both username and password, they are correct.

So, any ideas?

Oh, and apart from this I really love Kubuntu  :)

---

### Post by mindspin on 2005-05-11
what about the mtu rate ? 

I'm using dsl and it may differ, but in /etc/ppp/dsl-prvider I can find:

# Use the pppoe program to send the ppp packets over the Ethernet link
# This line should work fine if this computer is the only one accessing
# the Internet through this DSL connection. This is the right line to use
# for most people.
pty "/usr/sbin/pppoe -I eth1 -T 80 -m 1452"

# If the computer connected to the Internet using pppoe is not being used
# by other computers as a gateway to the Internet, you can try the following
# line instead, for a small gain in speed:
#pty "/usr/sbin/pppoe -I eth1 -T 80"

# An even more conservative version of the previous line, if things
# don't work using -m 1452...
#pty "/usr/sbin/pppoe -I eth1 -T 80 -m 1412"

/etc/ppp/provider says this:
These are the options to dial out to your default service provider.
# Please customize them correctly. Only the "provider" file will be
# handled by poff and pon (unless with extra command line arguments).

# You usually need this if there is no PAP authentication
noauth

# The chat script (be sure to edit that file, too!)
connect "/usr/sbin/chat -v -f /etc/chatscripts/provider"

# Set up routing to go through this PPP link
defaultroute

# Default modem (you better replace this with /dev/ttySx!)
/dev/modem

# Speed
38400

# Keep modem up even if connection fails
persist
###################

maybe its that........

this values are not taken from kubuntu, they are taken from debian/stable, but I guess that makes no difference.....

mindspin

---

### Post by wwwolf on 2005-05-11
[QUOTE=kevanf1]
So, any ideas?
 :)[/QUOTE]

I have your exact same problem. I can however get on-line using wvdial by setting it to run in Stupid Mode:

When wvdial is in Stupid Mode, it does not attempt to interpret any prompts from the terminal server. It starts  pppd  immediately  after  the modem connects.  Apparently there are ISPs that actually give you a login prompt, but work only if you start PPP, rather than logging in.  Go figure.  Stupid Mode  is  (naturally) disabled by default.

I also remember having to put K-internet in Stupid Mode while running SuSE.

I have yet to find out how to put KPPP into Stupid Mode but when we find this out I believe it will solve both our problems.

HTH,

---

### Post by wwwolf on 2005-05-11
here is what I did to get mine to work:

edit /etc/ppp/options  and take out the # on the line that says '#passive'

I also edited /etc/ppp/peers/kpp-options and placed 'noauth' in the file.

kppp now works for me but I can't find a system icon in the system tray anywhere.

I guess in order to disconnect I will just have to kill the process. :-(

HTH,

EDIT: Oh, I see, it is a minimized window, not a sys icon. Oh well......

---

### Post by kevanf1 on 2005-05-12
[QUOTE=wwwolf]here is what I did to get mine to work:

edit /etc/ppp/options  and take out the # on the line that says '#passive'

I also edited /etc/ppp/peers/kpp-options and placed 'noauth' in the file.

kppp now works for me but I can't find a system icon in the system tray anywhere.

I guess in order to disconnect I will just have to kill the process. :-(

HTH,

EDIT: Oh, I see, it is a minimized window, not a sys icon. Oh well......[/QUOTE]

Well I have tried those....still will not work. It still dies as soon as it asks for the password.  I have noticed that I get an error message about etc/resolve.conf file.  Apparently it can't read or see it.  Ok, tried to change permissions on it....erm, how?  When I cannot log in as root and su just does not do it.  I can't devote much more time to this as I've already let some jobs slide.  As a last resort I may try looking at the Ubuntu guide to setting up dial in.  I followed that with Ubuntu and got it working.  But does that only apply to a Gnome desktop?

---

### Post by wwwolf on 2005-05-12
[QUOTE=kevanf1]Well I have tried those....still will not work. It still dies as soon as it asks for the password.  I have noticed that I get an error message about etc/resolve.conf file.  Apparently it can't read or see it.  Ok, tried to change permissions on it....erm, how?  When I cannot log in as root and su just does not do it.  I can't devote much more time to this as I've already let some jobs slide.  As a last resort I may try looking at the Ubuntu guide to setting up dial in.  I followed that with Ubuntu and got it working.  But does that only apply to a Gnome desktop?[/QUOTE]

When you want to do something as root you first type a prefix to the command.
This prefix is 'sudo' which stands for "super user do".

ex: sudo chmod 777 /etc/resolve.conf
ex: sudo rm /directory/file-to-be-removed-that-only-has-root-permissions
etc.

1. You might also try running 'wvdialconf' to have it recognize your modem, then edit /etc/wvdial.conf to put in your phone #, username, and password.

2. You can also try 'pppconfig isp' and then go through the menu to set things up then to connect you run 'pon isp'

3. You could also try (after you finish setting up isp from pppconfig):
'pppd call isp'

There are probably 193 other ways to connect as well but these are the ones I can think of right now.

HTH,

---

### Post by kevanf1 on 2005-05-12
[QUOTE=wwwolf]When you want to do something as root you first type a prefix to the command.
This prefix is 'sudo' which stands for "super user do".

ex: sudo chmod 777 /etc/resolve.conf
ex: sudo rm /directory/file-to-be-removed-that-only-has-root-permissions
etc.

1. You might also try running 'wvdialconf' to have it recognize your modem, then edit /etc/wvdial.conf to put in your phone #, username, and password.

2. You can also try 'pppconfig isp' and then go through the menu to set things up then to connect you run 'pon isp'

3. You could also try (after you finish setting up isp from pppconfig):
'pppd call isp'

There are probably 193 other ways to connect as well but these are the ones I can think of right now.

HTH,[/QUOTE]


Okey dokey.  Dial up is working...WAHEY :-)))))  This is what I did in case any body needs to know.

Firstly I sorted out logging in as root (despite it being a bad idea sudo just wasn't doing the job).  Open up a terminal and type:

sudo passwd root
<enter su password here & hit return>

<now enter a password for root & again hit return>
<do that last step again to confirm>
<now quite the console>

Now you can log in as root and I found I had to go into /etc and create a text file called resolv.conf  Don't get confused with the folder named resolvconf (note the lack of a fullstop in the middle) it caught me out for a while.

Now, somebody had mentioned not being able to have an icon in the system tray.  If you open up KPPP configuration and go to the Misc tab all that is needed is to tick 'Dock into panel on connect', 'Minimize window on connect' and finally tick 'Quit on disconnect' otherwise you get the connection screen as soon as you have finished.

I also had to lower the speed settings in the modem tab.  At the highest speed available I was only getting a 9600kbps rate.  I dropped it down a couple of notches and am now getting around 50,000kbps.

Hopefully this will help somebody else  :)

---

