---
title: "Evolution-mapi working or not?"
date: 2009-03-08
forum: Desktop Environments
---

### Post by glauco.b on 2009-03-08
Hello all

I'm struggling to make the evolution-mapi plugin work in Jaunty. Don't know if this topic has been covered in other threads 'cause i looked for this several times and I've always found partial/unsolved bug reports.

Here is the problem:
1- I'm trying to connect with an exchange 2007 server with mapi
2- The mapi plugin loads correctly in evolution
3- After configuring the server parameter and clicking on "authenticate" to check the credentials the whole evolution crashes with a segfault

This happens always, even after several pakage updates, including samba4 on which the plugin is based.

The exchange server works, the connection parameters are ok, mapi is enabled on the server. Are there any other thigs I should check?

But, most important: somebody has got it working somewhere??? 

TNX

The crash log is this one:

```

** (evolution:15499): DEBUG: Loading Exchange MAPI Plugin 

** (evolution:15499): DEBUG: MAPI listener is constructed with 0 listed MAPI accounts 
** (evolution:15499): DEBUG: mailto URL command: evolution %s
** (evolution:15499): DEBUG: mailto URL program: evolution
Create profile with XXXXX YYYYYY xx.yyy.it ----hidden for privacy...----
libexchangemapi-Message: exchange-mapi-connection.c:2880: exchange_mapi_create_profile: lock(connect_lock)
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Logging into the server... succeeded 
libexchangemapi-Message: exchange-mapi-connection.c:146: exchange_mapi_connection_close: lock(connect_lock)
Segmentation fault (core dumped)

```

---

### Post by fuchur on 2009-03-08
It does not work for me as well.
see also 

[https://bugs.launchpad.net/ubuntu/+bug/319400](https://bugs.launchpad.net/ubuntu/+bug/319400)
and
[http://bugzilla.gnome.org/show_bug.cgi?id=571579](http://bugzilla.gnome.org/show_bug.cgi?id=571579)

none of these links unfortunately contain ny solution

---

### Post by glauco.b on 2009-03-08
That's what I found also

This is kind of ridiculous

Everybody else was asking for a mapi connector a few months ago. Now it is available, it doesn't work and, guess what? Nobody cares...

Well, we can only wait for someone to fix it...:(

---

### Post by wardin on 2009-03-11
Same EXACT status as you both just thought I'd confirm the issue....so close yet so far away! I don't think my backtraces will help anymore than what has already been posted here and on launchpad. But I'll attach mine in any case since I saw some weird key-ring password notices also.

Maybe the next release will have this kinked out and won't create newer issues :D

------------------------

---

### Post by wardin on 2009-03-12
Ok I got some result. I setup the account but did not complete authentication. Closed out of evol and came back.

This is what I get > [http://pastebin.ca/1359353](http://pastebin.ca/1359353)

Setup: Evolution 2.25.92 - Ubuntu release. Connecting to Exchange 2007.

I checked the OWA and have set the connection server to the server which supposedly has my user mailbox and also tried to use the main server that auths and redirects to the server with the mailbox. Also tried ip addresses instead regular entries. All end up with the above pastebin result.

~

---

### Post by coutts99 on 2009-03-19
I get the same, however, I tired creating a blank account, then once Evolution started changing this account to connect to Exchange via MAPI.

Now when I start Evolution it shows my folders and how many new messages are in them, but the folders are empty when I click on them and I get this error on the console -:
> 
(evolution:20300): camel-mapi-provider-WARNING **: Unable to load summary no such table: Mailbox - Someone/Inbox.

Very frustrating!

---

### Post by dhuptas on 2009-03-19
I assume that's due to the following bug:

[http://johnnyjacob.wordpress.com/2009/03/19/evolution-mapi-update-release-02601/](http://johnnyjacob.wordpress.com/2009/03/19/evolution-mapi-update-release-02601/)

---

### Post by coutts99 on 2009-03-19
Removed evolution-mapi and downloaded and built it from that link, still same error :(

---

### Post by sweetsinse on 2009-03-19
was having the same problem until i found this page.

i used:

sudo -s
mkdir evomapi
cd evomapi/
apt-get install dpkg-dev fakeroot
apt-get build-dep evolution-mapi
apt-get source evolution-mapi

--------------->
edit all the files from the patch accourdingly.
[http://bugzilla.gnome.org/attachment.cgi?id=130818&action=view](http://bugzilla.gnome.org/attachment.cgi?id=130818&action=view)
i used vim and did it manually on each file with this:

%s/G_GUINT64_FORMAT/G_GINT64_MODIFIER/g

ALSO EDIT debian/changelog!!!!
--------------->

fakeroot apt-get -b source evolution-mapi
dpkg -i *.deb

now mine works fine.  still working on GAL and calendars though.

---

### Post by coutts99 on 2009-03-20
> **sweetsinse said:**
> was having the same problem until i found this page.

i used:

sudo -s
mkdir evomapi
cd evomapi/
apt-get install dpkg-dev fakeroot
apt-get build-dep evolution-mapi
apt-get source evolution-mapi

--------------->
edit all the files from the patch accourdingly.
[http://bugzilla.gnome.org/attachment.cgi?id=130818&action=view](http://bugzilla.gnome.org/attachment.cgi?id=130818&action=view)
i used vim and did it manually on each file with this:

%s/G_GUINT64_FORMAT/G_GINT64_MODIFIER/g

ALSO EDIT debian/changelog!!!!
--------------->

fakeroot apt-get -b source evolution-mapi
dpkg -i *.deb

now mine works fine.  still working on GAL and calendars though.


Yay thanks it works!

You can save the patch file as patch.diff in the unpacked evolution-mapi directory then do -

```
patch -p0 < patch.diff
```

---

### Post by coutts99 on 2009-03-20
Hmm, message subjects seem to be blank :)

---

### Post by clayton on 2009-03-20
> ALSO EDIT debian/changelog!!!!

Could you please explain what part of this file to edit?

---

### Post by coutts99 on 2009-03-20
I didn't change it :)

---

### Post by glauco.b on 2009-03-20
> **coutts99 said:**
> Yay thanks it works!

You can save the patch file as patch.diff in the unpacked evolution-mapi directory then do -

```
patch -p0 < patch.diff
```

Ok, I did everything, but still no luck, after clicking on "authenticate" when creating the account i still get the same exact error as before

```

Logging into the server... succeeded 
libexchangemapi-Message: exchange-mapi-connection.c:146: exchange_mapi_connection_close: lock(connect_lock)

```

Plus: I just upgraded to gnome 2.6 and everything is the latest available version.


I'm giving up. Some day I guess it will magically start working

---

### Post by clayton on 2009-03-20
Same here. The latest update today (0.26.0.1-0ubuntu1) of evolution-mapi resulted in the same crash while trying to connect. I'll keep my fingers crossed for the jaunty-proper release.

---

### Post by coutts99 on 2009-03-23
I had to create a new blank account, then once evolution opens, go back and change it to a mapi account and fill in the details then.

---

### Post by clayton on 2009-03-23
Thanks for the advice, coutts99. I created the blank account then went back and put my exchange server info in. Evolution froze and I forcefully closed it. Every time I restarted Evo, it would crash within 2 seconds (checking exchange server mail).

I uninstalled and reinstalled evolution, and now it doesn't crash but it fails login with this output (no password in keyring?):
```
bash: evollution: command not found
clayton@lappy3:~$ evolution
** (evolution:4645): DEBUG: Loading Exchange MAPI Plugin 

** (evolution:4645): DEBUG: MAPI listener is constructed with 1 listed MAPI accounts 
** (evolution:4645): DEBUG: mailto URL command: evolution %s
** (evolution:4645): DEBUG: mailto URL program: evolution
e-data-server-ui-Message: Unable to find password(s) in keyring (Keyring reports: No matching results)
e-data-server-ui-Message: Key file does not have group 'Passwords-ExchangeMAPI'
libexchangemapi-Message: exchange-mapi-connection.c:130: exchange_mapi_connection_new: lock(connect_lock)

exchange-mapi-connection.c:75: Entering mapi_profile_load Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
    GetDefaultProfile        : MAPI_E_NOT_FOUND (0x8004010F)

exchange-mapi-connection.c:116: Leaving mapi_profile_load libexchangemapi-Message: exchange-mapi-connection.c:133: exchange_mapi_connection_new: unlock(connect_lock)

(evolution:4645): libexchangemapi-WARNING **: 
exchange-mapi-connection.c:136: exchange_mapi_connection_new: Login failed 
e-data-server-ui-Message: Unable to find password(s) in keyring (Keyring reports: No matching results)
e-data-server-ui-Message: Key file does not have group 'Passwords-ExchangeMAPI'
```

any ideas?

---

### Post by coutts99 on 2009-03-24
> **clayton said:**
> Thanks for the advice, coutts99. I created the blank account then went back and put my exchange server info in. Evolution froze and I forcefully closed it. Every time I restarted Evo, it would crash within 2 seconds (checking exchange server mail).

I uninstalled and reinstalled evolution, and now it doesn't crash but it fails login with this output (no password in keyring?):

any ideas?

Not sure, mine works fine for checking email. Have you gone back into the options and put your password in again?

Lot's of bugs in the software though, so I'm sticking to using Outlook over Citrix for now. I'll keep revisiting it though, as I'd rather just use Evolution.

---

### Post by evanjfraser on 2009-03-24
Hi guys, I'm getting the same segfault and I was wondering if you need to setup kerberos and connect to the domain before the above fix works?

Cheers, Evan.

---

### Post by coutts99 on 2009-03-24
> **evanjfraser said:**
> Hi guys, I'm getting the same segfault and I was wondering if you need to setup kerberos and connect to the domain before the above fix works?

Cheers, Evan.

I didn't do that.

---

### Post by brianbourke75 on 2009-03-26
I am having the same issues as posts above.  This is VERY important to me because my work uses exclusively exchange server, as I would imagine many people's work do.  Hopefully I will not have to start making sacrifices to the Gods.  

Thanks in advance!

---

### Post by dwarness on 2009-03-26
I would just like to add that when trying to configure evolution-mapi on my system, I encountered the exact same issues as shown in the log files that have been posted here.  I followed the above instructions for downloading the source, only to find that the changes had already been applied.

Figuring that the source packages may be more recent than the current deb packages in repository, I compiled the source packages and installed them.  I still get the exact same error.

Soo close, and yet .. soo far.

---

### Post by xtoudi on 2009-03-29
info from MAPI FAQ:

[I][B]..." I've specified all the details correctly, but I'm unable to get past the Authentication?

Please make sure:

    * Your mailbox is enabled for MAPI (This is a setting on the server).
    * Your Exchange server has Public Folders set up (There have been some issues observed if there is no PF hierarchy setup on the server). "...[/B][/I]

[http://www.go-evolution.org/MAPI_FAQ#Compiling_from_source](http://www.go-evolution.org/MAPI_FAQ#Compiling_from_source)

And if you want to play with compiling:
[http://www.go-evolution.org/MAPIProvider](http://www.go-evolution.org/MAPIProvider)

---

### Post by Balachmar on 2009-03-30
Right now it seems that is should work, but memory consumption is killing it. 2.3G in a computer with 750M RAM and 1G SWAP....

---

### Post by wardin on 2009-03-31
Current Status. Fail!
> [http://www.pastebin.ca/1377949](http://www.pastebin.ca/1377949)

---

### Post by gnipper on 2009-04-02
For what it's worth I followed coutts99's method and I have email working using MAPI. I had the same problem of crashes when I tried to set up a MAPI account using the wizard. 

I don't seem to be able to pick up the calendar from Exchange though - it just shows a blank calendar on my local machine. Same for contacts - nothing to see. I'm using Xubuntu Jaunty with Exchange Server 2007.

---

### Post by RagingAardvark on 2009-04-23
Using IP addresses I got the account set up. However, I suffer from the out of memory too - to about 2gig and then keels over. 

Heaven alone knows what it's doing to chew through that much memory.

---

### Post by defishguy on 2009-04-23
I got it to work following this [_bug report here_]("https://bugs.launchpad.net/ubuntu/+source/evolution-mapi/+bug/340532").

> sudo cp /etc/samba/smb.conf smb.conf.backup
> sudo rm /etc/samba/smb.conf

Restart Evolution....

Enter whatever account information applies...

I then restored smb.conf

> sudo cp /etc/samba/smb.conf.backup smb.conf

Everything seems to be working okay now.

Update 25 April 2009..... I ended up having to remove smb.conf altogether in order to make it work consistently.

---

### Post by mr_raider on 2009-04-25
I just upgraded from Intrepid to Jaunty and I notice that Evolution can now connect to my MS Exchange 2007 server in Exchange mode (not IMAP). I notice that the evolution-mapi plugin is not installed in synaptic. Has their been an upgrade to Evolution?

Also my contacts, tasks and calendars stnc up, but not my notes. Any ides?

---

### Post by jsfarrow on 2009-04-27
I'm having similar problems with evolution-mapi after upgrading to Jaunty. This is evolution-mapi 0.26.0.1-0ubuntu2.

When I input my account info and press the authenticate button, I get a segfault (user and servername changed in below output):


$ evolution
** (evolution:13500): DEBUG: Loading Exchange MAPI Plugin 

** (evolution:13500): DEBUG: MAPI listener is constructed with 0 listed MAPI accounts 
** (evolution:13500): DEBUG: mailto URL command: evolution %s
** (evolution:13500): DEBUG: mailto URL program: evolution
** (evolution:13500): DEBUG: EI: SHELL STARTUP
EI: MAIL PREFSe-data-server-ui-Message: Unable to find password(s) in keyring (Keyring reports: No matching results)
e-data-server-ui-Message: Key file does not have group 'Passwords-ExchangeMAPI'
Create profile with username companyname BRM-EXCH-1.corp.companyname.com
libexchangemapi-Message: exchange-mapi-connection.c:2874: exchange_mapi_create_profile: lock(connect_lock)
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Logging into the server... succeeded 
libexchangemapi-Message: exchange-mapi-connection.c:146: exchange_mapi_connection_close: lock(connect_lock)
Segmentation fault

I guess I was too quick to believe the Jaunty reviews that Exchange support was now 'rock solid'. :( 

Anyone else seeing this?

- Scott

---

### Post by muecker on 2009-04-27
I think it is partially working, but extremely buggy.  Using the IP address, Evolution will connect to my Exchange server and some of the folders show up but I have not successfully downloaded any emails yet.  I have also noticed the memory continues to climb and it has crashed multiple times.  I can only assume it is either trying to put all of my mail into memory or there is a serious memory leak (or both).

I have tried running it overnight but when I look at my machine the next morning Evolution has shut itself down.

I have been looking for this one feature to appear in Evolution for the last two releases and now that it has, it doesn't work.  Considering the issues I have had with the ATI video in my laptop, I really wish I wouldn't have upgraded to Jaunty.  I didn't get the features I wanted and I lost features I already had.

---

### Post by mr_raider on 2009-04-27
I've been able to connect to my exchange 2007 server without using the Mapi plugin, just standard MS Exchange account config.

---

### Post by exterminatus on 2009-04-28
I guess we are a lot of people who follow this question since it's a key for Ubuntu to be a serious replacement for Windows.

I did get mail to work by deleting the /etc/samba/smb.conf file and starting with an empty e-mail account. Still i did not get calendar, contacts, notes and tasks.

But its a good start. All cred to the people working with the MAPI-plugin.

The only thing a miss about my old Vista installation is actually Outlook which has been my friend for so many years (Vista though pushed me to do this try for Ubuntu)

/m

---

### Post by coutts99 on 2009-04-28
Just updated evolution mapi from svn, and I can now reply to emails (i.e. the email address from internal people gets filled in properly) :) Hooray!

---

### Post by coutts99 on 2009-04-28
> **mr_raider said:**
> I've been able to connect to my exchange 2007 server without using the Mapi plugin, just standard MS Exchange account config.

Just tried that and doesn't work for me

---

### Post by derelict888 on 2009-04-28
I was able to setup an account using the MAPI connector by using the exchange server's IP address, not its DNS name. That worked initially but has not worked since. Some might find this works, you also might want to edit your /etc/nsswitch.conf file;

```
hosts:          files dns [...]
```

That worked for me initially, maybe that will help some others so we can get to a resolution quicker. Having evolution fully working on an exchange server would be a HUGE step forward for migrating Windows users over.

---

### Post by mr_skater99 on 2009-04-28
> **coutts99 said:**
> Just updated evolution mapi from svn, and I can now reply to emails (i.e. the email address from internal people gets filled in properly) :) Hooray!

Just got setup using exchange-mapi.  Using ip of exchnage box im good to revieve.

But everything i send i get and error email back from exchange saying:


username
The recipient's e-mail address was not found in the recipient's e-mail system. Microsoft Exchange will not try to redeliver this message for you. Please check the e-mail address and try resending this message, or provide the following diagnostic text to your system administrator.

Where username is the internal users logon (ie u123456) instead of [email]joe.bloggs@company.com[/email]

Is this fixed with the latest svn update?

---

### Post by muecker on 2009-04-29
The interesting thing is that I have heard the Evolution plugin is based on the OpenChange plugin.  Yesterday I installed the openchangeclient package and I can use it to retrieve my mail.  It isn't automated, dumps its output to the command line, etc. but it will at least read the mail headers.  Why can't they get Evolution right using those same libraries or are they just not using the latest package?

---

### Post by muecker on 2009-04-29
Now this is interesting.  I started Evolution from the command line.  From what I can tell, it is scanning hundreds of folders I have never heard of before.  I don't think these are public folders, I think its looking at every folder on the server.  Its no wonder it is unable to retrieve my mail.  Anybody know how to limit the list to what it should be?

---

### Post by coutts99 on 2009-04-29
> **mr_skater99 said:**
> 
Where username is the internal users logon (ie u123456) instead of [email]joe.bloggs@company.com[/email]

Is this fixed with the latest svn update?

I thought it was, but it isn't :)

Back to using Citrix :)

---

### Post by derelict888 on 2009-04-29
I'm not often a donor (more like never), but if donating means the evo-mapi connector will work correctly and allow Evolution to operate comparable to outlook (mail/contacts/calendar) I'll gladly do so. As a Sys Admin I use Ubuntu/Linux but I never recommend it for any other users; almost always on the premises of no outlook replacement. Fully functioning email on an exchange server is the missing link in my hopes to move places I work away from Windows, keep up the good work. Now that the lid on Pandora's box has been cracked open, lets take the lid off entirely. :guitar:

---

### Post by mr_skater99 on 2009-04-29
Yeah - i can receive email fine (using ip address of exchange box - not dns name).

And sending outside organisation is ok - but inside its not.

Still chewing a lot of memory.  And is a little buggy in general (which i can totally live with).

Will go back to OWA - just until the next fix is upstream.

Its a lot closer than it has been in the past!

---

### Post by !nkubus on 2009-04-30
The IP trick worked for me :D

I'm able to send and receive, but sometimes it hangs, well we are getting closer.

---

### Post by mr_raider on 2009-05-02
> **mr_skater99 said:**
> 

Will go back to OWA - just until the next fix is upstream.

Its a lot closer than it has been in the past!

Can you get full fucntionality in OWA in firefox? I only get the limited interface.

---

### Post by derelict888 on 2009-05-04
Has anyone tried the PST import? Maybe importing the PST helps evolution run more smoothly?

---

### Post by bszmyd on 2009-05-06
> Why can't they get Evolution right using those same libraries or are they just not using the latest package?
Having worked with the libmapi library myself I can tell you the whole thing is VERY clumsy. Microsoft did a horrible (or excellent depending on how you look at it) designing the protocol making it very obfuscated.

That coupled with the fact that libmapi doesn't have the greatest documentation and, to my knowledge, based on code from the new rewrite of Samba which is still buggy doesn't surprise me that writing an Evolution plug-in is indeed a difficult task. It took me months to get my plugin written for a project here at work to stop seg-faulting and actually work, and all it did was parse your Inbox! Good luck guys!

---

### Post by psorcerer on 2009-05-21
Err... segfaults just fine with IP or FQDN. Unusable.

---

### Post by wolfteeth on 2009-06-29
May I know the detailed configuration of the Evolution+Mapi+Exch2007? cuz I can get mails correctly but unable to sent mail or reply mails, all email address become to the alias, error is: #550 5.1.1 RESOLVER.ADR.ExRecipNotFound; not found ##

---

### Post by Chambers on 2009-07-08
Hey guys, can someone tell me what file I need to edit to get this working.  Here's my problem.  

For Server I put in: servername.domain.com
username: myusername

Now, when I click authenticate it tries to authenticate to;

[email]myusername@servername.domain.com[/email]

I need it to authenticate as [email]myusername@domain.com[/email]

I think this is why it never takes my password.

Also, does rpc+https work with this connector yet?

I've tried googling this stuff left and right and can't find anyone asking these questions, thanks!

---

### Post by stmiller on 2009-09-23
evolution-mapi has just been updated in Karmic (today 9/23). Please give it a shot!

---

### Post by mr_skater99 on 2009-09-23
I'm not sure how this works - I'd like to try it in jaunty.  Is it in proposed or something similar?

---

### Post by mr_skater99 on 2009-09-23
I upgraded to Karmic on one of the VM's.

All updated - but now no matter what combination of server /username i try i can't get it to authenticate.

I have tried fqdn of server as well as ip address.

And for user name i have tried domain\username, username, DOMAIN\username etc

Anyone got any ideas?

---

### Post by dave100 on 2009-09-24
I managed to get through the authentication in account setup page. With hostname (not IP), username and domain in separate fields.

But evolution-mapi is still useless. Mail listing has empty From and Subject columns for most of my mails. And in preview or in opened message the content text is missing and replaced by "[?]"

Calendar view looked fine at first glance, but after opening an item, it caused a crash report.

Maybe (hopefully) these are character set problems, I'm Scandinavian. Just upgraded to evolution-mapi 0.28.
 
Well, back to owa for calendaring:(

---

### Post by stmiller on 2009-10-03
Evolution-mapi works on Fedora 11, and now Fedora 12 is coming out soon. I wish Ubuntu had worked to make evolution-mapi more of a priority, being a desktop-oriented distro. :/

This is a missed opportunity- oh well.

---

### Post by mr_raider on 2009-10-06
Got it to authenticate in karmic beta, and loaded the email folders fine. However it crashes every time I try to open a message. Calendar entries are off by 3 hours.

I guess it's progress. In Jaunty I couldn't get anything done.

---

### Post by HDave on 2009-10-22
Wow this is depressing.  I've been waiting for this for 18 months hoping Karmic would solve these problems.  

Like the others, I seem to be able to use the openchange command line tools just fine...  The problem is in the Evolution connector -- how crazy is this??  100% of the heavy lifting is done and working and we all can't ditch outlook because of some misc bugs in the connector!  Argggg! :-(

Edit:  A recent status report from the openchange folks made at the recent samba conference can be found [here.]("http://www.openchange.org/index.php?option=com_content&task=view&id=64&Itemid=72#sambaxp_2009")

---

### Post by farbror_ace on 2009-10-23
Signing the solution with using IP address instead of DNS name of the server.
Works for me.

---

### Post by Scabby_al on 2009-10-30
I can get mine to authenticate using the IP but when I try to read a message, it crashes every time. I also can't use the OWA evolution-exchange plugin because it isn't compatible with Exchange 2007. 

I'm not switching to Fedora because I can't stand that distro but I do envy their mapi-plugin actually working.

---

### Post by tmugan on 2009-11-13
I'm able to use Exchange 2007 under Karmic if I grab the latest updates to the MAPI plugin and install manually.
(It has not been added to the Ubuntu repos yet for Karmic.)

Follow the steps here...

[http://www.mugan.com/2009/11/03/usin...exchange-2007/]("http://www.mugan.com/2009/11/03/using-evolution-with-exchange-2007/")

---

### Post by mr_skater99 on 2009-11-15
Awesome!!

Any idea when this will be available in the repos?

---

### Post by mr_skater99 on 2009-11-15
I just tried this on a fresh update to date install of karmic.  I had not previously installed the mapi plugin from the repos on this install.

Install worked fine - however this plugin breaks evolutions setup assistant, in that it makes the forward button constantly greyed out.

So once the plugin was installed i couldnt get through the setup wizard to setup my exchange account - so i couldnt get into evolution.  I then removed the plugin - setup assistant works, so i setup a default account, and reinstalled the plugin.  Now i can get into evolution, though i would just change the account to have the exchange settings i need - but the evolution mapi plugin doesnt show up as an option....

So i installed the plugin from the repo, started evolution and setup my account.  I then killed evolution, uninstalled the plugin from the repo and re installed the plugin from source - and i can connect just fine.

I still however have the bug of only being able to send email out side of my organisation and not internally - "The recipient's e-mail address was not found in the recipient's e-mail system. Microsoft Exchange will not try to redeliver this message for you. Please check the e-mail address and try resending this message, or provide the following diagnostic text to your system administrator."

So after all that , unfortunately i am no closer to using evolution for exchange at work....  :(

---

### Post by Usufruct on 2009-11-24
I compiled and installed evolution-mapi 0.28.0 and I am not able to authenticate to my company's exchange server.  Evolution hangs for a couple minutes then gives a relatively generic authentication error.

---

### Post by Joseph Brown on 2009-11-24
I have the same issues as Skater99. I am able to connect and sync with Exchange 2007 mailbox server after recompling evolution-mapi-0.28 per previous post. I receive messages and can see GAL entries but when I send a message internally it returns a Undeliverable message: #550 5.1.1 RESOLVER.ADR.ExRecipNotFound; not found ##. Anyone have any ideas how to fix? Only does this in Evolution. Works fine in OWA and Outlook 2007 client.

---

### Post by linuxpark on 2009-11-26
I could get it working at last!
With Ubuntu Kramic + Evolution 2.28.1(with** evolution-mapi 0.28.1**) with MS Exch 2007

-----
i) 
Removed evolution-mapi version 0.28
[FONT=Courier New][SIZE=2]sudo apt-get remove evolution-mapi[/SIZE][/FONT]

ii)
Installed some dependencies:
[SIZE=2]*[FONT=Courier New][I]sudo apt-get install *evolution-data-server-dev libedataserverui1.2-dev libebackend1.2-dev libecal1.2-dev libedata-cal1.2-dev libedata-book1.2-dev libcamel1.2-dev[/FONT]

[/I][/SIZE][FONT=Courier New][SIZE=2]*[I]sudo apt-get install *evolution-dev libmapi-dev samba4-dev intltool[/I][/SIZE][/FONT]

iii) 
Downloaded, compiled and installed Evolution-mapi 0.28.1
[FONT=Courier New][SIZE=2]
cd /home/user/evolution-mapi/
wget [http://download.gnome.org/sources/evolution-mapi/0.28/evolution-mapi-0.28.1.tar.bz2](http://download.gnome.org/sources/evolution-mapi/0.28/evolution-mapi-0.28.1.tar.bz2)
tar xvjf evolution-mapi-0.28.1.tar.bz2
cd evolution-mapi-0.28.1/

./configure
make
sudo make install[/SIZE][/FONT]

iv) Started Evolution, checked config and authentication success and 
And its [COLOR=DarkGreen]**[SIZE=3]WORKING...!![/SIZE]**[/COLOR] :)

Yet have to test other stuff like calenders etc.. will post back soon...

---

### Post by mr_skater99 on 2009-11-26
@linuxpark - can you send emails to others in your organisation - on your exchange server - or just external emails?

---

### Post by Kaya2 on 2009-11-26
With Ubuntu Kramic + Evolution 2.28.1(with** evolution-mapi 0.28.1**) with MS Exch 2007

I confirm that you can authenticate, read email and contact and calendar.
But i am not able to send email inside the domain.
I have also a another bug, the send mail are not store in the Sent folders.

according to the [Gnome bug list]("https://bugzilla.gnome.org/buglist.cgi?bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&bug_status=NEEDINFO&content=mapi&product=&query_format=specific&order=bug_severity%2Crelevance%20DESC&query_based_on="), the send email bug  id [568763]("https://bugzilla.gnome.org/show_bug.cgi?id=568763") should be fix but it is not.


Also to authenticate you need to use the fqn, otherwise you get a network error.

Thanks

---

### Post by linuxpark on 2009-11-26
Kaya2,

May be I got too excited after seeing it authenticating and seeing my mail box downloading in Evolution... But hmm :(
(Btw, Exchange and MS Office Comm 2007 are the only two things stopping me to completely forget windows)

Yes, on closer look I too face similar issues and one more issue, like..
the Evolution is in a loop.... always the status bar shows 
"Retrieving message ID's from server for inbox (xx% complete)"
and "Retrieving message xxxxxxxxxxxxxxxxxxx" for hours like in infinite loop...
My mail box size is big , but this happening for 3/4 hours is something funny...

o/g mails I checked to myself it worked and to gmail it worked, but when I sent it to  others in my domain didn't work.

And, Calender, I don't see any meetings/events.
Global address book is nill.

---

### Post by Kaya2 on 2009-11-26
Good news i made it.
The patch for bug id [568763]("https://bugzilla.gnome.org/show_bug.cgi?id=568763") was not include in the 0.28.1 release.

Shutdown evolution
Create the path file:
# wget "http://bugzilla-attachments.gnome.org/attachment.cgi?id=148155"  -O 568763.diff
# patch -p1 < 568763.diff
# make clean
# ./configure
# make
# sudo make install

relaunch evolution, send an email and it is magic.
Now i can go back to work after loosing 2 days after the exchange migration.

---

### Post by MrSqueezles on 2009-11-30
Thanks, everyone!  I now have access to email and can email internally.  I still can't see the address book or calendar, but I think I can get along with OWA for those until evolution-mapi is improved.

Here's the process I followed after having tried evolution-mapi, installed through Synaptic.
```
$ cd
$ sudo apt-get remove evolution-mapi
$ sudo apt-get install evolution-data-server-dev libedataserverui1.2-dev libebackend1.2-dev libecal1.2-dev libedata-cal1.2-dev libedata-book1.2-dev libcamel1.2-dev
$ sudo apt-get install evolution-dev libmapi-dev samba4-dev intltool
$ wget http://download.gnome.org/sources/evolution-mapi/0.28/evolution-mapi-0.28.1.tar.bz2
$ tar xvjf evolution-mapi-0.28.1.tar.bz2
$ cd evolution-mapi-0.28.1/
$ wget "http://bugzilla-attachments.gnome.org/attachment.cgi?id=148155" -O 568763.diff
$ patch -p1 < 568763.diff
$ ./configure
$ make
$ sudo make install
```

---

### Post by mr_skater99 on 2009-12-02
I managed to get it working - temporarily.

I could send email internally, albeit for about 5 mins!!!

I then shut evolution did some stuff and went back and it wouldn't authenticate me to the exchange server any more....

I did some un-installing and re-installing and got the same thing a few times - worked first go, and then wouldn't authenticate after shutting and starting evolution.

But definitely progress!!!!

---

### Post by abhi.datt on 2009-12-02
If I follow the steps sent by Kaya, I get no errors but when I launch Evolution wizard, all Forward buttons are disabled. Is anyone else facing this issue??

Oops! I missed this completely 
[http://ubuntuforums.org/showpost.php?p=8323845&postcount=61](http://ubuntuforums.org/showpost.php?p=8323845&postcount=61)

---

### Post by rchille on 2009-12-04
All right! I have Evolution tied to Exchange via the 0.28.1 plugin.

I can send/receive email, however, I'm missing calendar and GAL support. The calendar shows nothing though tracing through the logs evolution can "see" to entires: 

```
|---+ Calendar        : (Container class: IPF.Appointment 1D9894311D000001) UnRead : 0 Total : 2 size : 5657

```

Whenever I go to add an entry to the Calendar I get a "Unable to open the calendar: Calendar" message in a pop up.

GAL is just blank.

Any suggestions?

---

### Post by MrSqueezles on 2009-12-07
> **rchille said:**
> All right! I have Evolution tied to Exchange via the 0.28.1 plugin.

I can send/receive email, however, I'm missing calendar and GAL support.
I haven't gotten calendar working reliably.  Some meetings show up, but others don't.  If I accept any calendar invitations or try to add an event, things disappear or shift around.  I've been using web mail for meetings (painful) and Evolution for everything else.

The address list is very, very slow and can take 10 to 30 seconds to show up at first.  Performing searches is relatively fast, though.  It didn't show up for me at all until I rebooted for the first time after installing through the instructions I described before.

Actually, now that I've thought about it.  The calendar didn't work at all either until I had rebooted once.

---

### Post by jmarks on 2010-01-02
After following the instructions posted above, I have successfully tied Evolution to Exchange via the 0.28.1 plugin.
I can authenticate to the server and see all my folders. There is a major problem, however, with accessing email messages: I can read any new message once. The problem is that, with some messages, accessing them a second time in the Inbox shows the headers, but no email message. The text box containing the message is not shown.

Exiting and restarting Evolution and reconnecting to the server does refresh the list of messages, but does not change the status of those messages for which the only the headers remain. 
Accessing my mailbox through the web owa interface shows those "missing" messages to be intact. 
Is there a way to get Evolution to access those missing messages again?

Two other smaller issues:
1.  sent emails in the Outbox do not show to whom they were sent.
2. When I reviewed an email I sent in the Outbox, I found that it was presented in Japanese. (I typed it in English).  Accessing the same email via the web interface does, in fact, show it in Japanese, so I suspect that was how it was encoded and sent. A subsequent email I sent was in Englsh and encoded correctly.

Has anyone had these experiences, or can suggest ways to debug this? Worthy of bug reports?
thanks!

---

### Post by devinfriday on 2010-01-18
Hi,

> **jmarks said:**
> After following the instructions posted above, I have successfully tied Evolution to Exchange via the 0.28.1 plugin.
I can authenticate to the server and see all my folders. There is a major problem, however, with accessing email messages: I can read any new message once. The problem is that, with some messages, accessing them a second time 
in the Inbox shows the headers, but no email message. The text box containing the message is not shown.

I am in the same situation as you, except, the missing body happens only for some mails (sent from the same guy!!!). 

> 
Exiting and restarting Evolution and reconnecting to the server does refresh the list of messages, but does not change the status of those messages for which the only the headers remain. 
Accessing my mailbox through the web owa interface shows those "missing" messages to be intact. 
Is there a way to get Evolution to access those missing messages again?


I hope so...

> 
Two other smaller issues:
1.  sent emails in the Outbox do not show to whom they were sent.
2. When I reviewed an email I sent in the Outbox, I found that it was presented in Japanese. (I typed it in English).  Accessing the same email via the web interface does, in fact, show it in Japanese, so I suspect that was how it was encoded and sent. A subsequent email I sent was in Englsh and encoded correctly.


Not happened.. yet... but after a while my evolution client seems to "freeze" not allowing me to download new messages. Closing and restarting seems to work.
[/QUOTE]

I will be happy to provide further assistance to developers/debuggers to solve this.

---

### Post by shrinkpad on 2010-01-20
I really don't understand the thinking of Ubuntu here. 

Perhaps it's openchange which is holding things up, but exchange compatibility (mail, calender, contacts, everything GAL based) is a lynch pin for most major companies porting their desktops to Linux. Like it or loath it, it's a fact that exchange is here to stay for the near future and if you work for a corp like me (telecoms) you have no choice but to use it.

When MAPI compatibility finally made it into a stable release their was a big fanfare on finally being able overcome this obstacle only for it to turn about to be a buggy, half functioning mess. 

A year on I download 9.10 and expect to be able to configure an out of box exchange account, but instead I find users still struggling with different versions and finding half the functionality is still broke, some even resorting to compiling code from different sources.

If the technically minded such as us struggle to get this going, what the hell is the average user going to make of this?

Don't get me wrong this is no issue for a 'geek' who likes tweaking there workstation and hacking around, but for someone who wants to get on with a job, it's a right pain in the ***.

---

### Post by jmarks on 2010-01-20
> **shrinkpad said:**
> I really don't understand the thinking of Ubuntu here. 
When MAPI compatibility finally made it into a stable release their was a big fanfare on finally being able overcome this obstacle only for it to turn about to be a buggy, half functioning mess. 

A year on I download 9.10 and expect to be able to configure an out of box exchange account, but instead I find users still struggling with different versions and finding half the functionality is still broke, some even resorting to compiling code from different sources.


I remain very discouraged. If you look at the evolution-mapi bugs reported, they seem to all be graded very low on the urgency scale. If I really want to commit to Linux than I need to run Windows as a virtual machine all the time, because there is no decent outlook mapi support. And then -- what's the point?

---

### Post by shrinkpad on 2010-01-20
> **jmarks said:**
> I remain very discouraged. If you look at the evolution-mapi bugs reported, they seem to all be graded very low on the urgency scale. If I really want to commit to Linux than I need to run Windows as a virtual machine all the time, because there is no decent outlook mapi support. And then -- what's the point?

I feel you bro. 

It's a joke it ever made stable. For near on 5 years I have walked around with dual boot laptops at work..I try and so desperately want to use Ubuntu, but's it's to painful using outlook web access when I get project managers sending invites for conference calls all day long in a packed out calendar.

It's better to just go back to using XP where I have the lot working and indexed by google desktop.

Granted a lot of the issue originates in the fact that MAPI is closed source, but that argument can no longer wash when you tend a product to the commercial sector with promises of full MS intergration (namely exchange).

---

### Post by HDave on 2010-01-20
The openchange group that created the mapi library is working off of the publicly documented web services API from Microsoft, so no excuses there.  Their progress is steady, but nearly glacial.

The Evolution plug-in on top of the openchange stuff is just plain terrible.

I gave up waiting and caring about a year ago.  

In my particular case, I set up a Funambol server to sync contacts and calendar between Exchange & Thunderbird/Evolution/etc and am using IMAP for emails.  The side benefit is there are hundreds of mobile phones with native sync to Funambol (which is open source).

---

### Post by kaput on 2010-01-27
I'm a recent hire (1 week) for a company with Exchange 2007. With the recent evolution-mapi 0.28.2 release, I'm able to get connected and things seem to be working.

However, people need to be sure to not be hitting a stand-alone OWA front-end. The evolution-mapi connector won't work without back-end access.

While I've not had time to fully explore potential issues, I have noticed that while the calendar does work it doesn't seem to be syncing/showing recurring appointments.

---

### Post by johan.vervloet on 2010-01-28
> **jmarks said:**
> After following the instructions posted above, I have successfully tied Evolution to Exchange via the 0.28.1 plugin.
I can authenticate to the server and see all my folders. There is a major problem, however, with accessing email messages: I can read any new message once. The problem is that, with some messages, accessing them a second time in the Inbox shows the headers, but no email message. The text box containing the message is not shown.

Exiting and restarting Evolution and reconnecting to the server does refresh the list of messages, but does not change the status of those messages for which the only the headers remain. 
Accessing my mailbox through the web owa interface shows those "missing" messages to be intact. 
Is there a way to get Evolution to access those missing messages again?


There seems to be a bug report for this: [https://bugs.launchpad.net/ubuntu/+source/evolution-mapi/+bug/502514](https://bugs.launchpad.net/ubuntu/+source/evolution-mapi/+bug/502514)

---

### Post by pavelchjen on 2010-01-29
I am running Ubuntu 9.10 karmic. And Evolution-mapi was not work for me from package repository. So I downloaded source code of newer exchange-mapi and GtkHTML compiled it and installed.
With provided package in repository I had issues with address book, it was not properly pars addresses so exchange was unable to send email to recipient in same domain as me, with returning code something like "Mail delivery problem unknown recipient". With new compiled version no issues.
Calendar works without issues with new compiled MAPI plugin unlike to existing package from rep where it was just crashed as soon as I open calendar.
What I did:
in terminal
evolution --force-shutdown
#Shutting down all evolution processes

mkdir ~/evolution
cd ~/evolution
#Downloading source code from gnome-evolution project page
wget [http://download.gnome.org/sources/evolution-mapi/0.28/evolution-mapi-0.28.2.tar.bz2](http://download.gnome.org/sources/evolution-mapi/0.28/evolution-mapi-0.28.2.tar.bz2)

wget [http://download.gnome.org/sources/gtkhtml/3.28/gtkhtml-3.28.2.tar.bz2](http://download.gnome.org/sources/gtkhtml/3.28/gtkhtml-3.28.2.tar.bz2)


#Removing evolution-MAPI package
sudo apt-get remove evolution-mapi
#
#Intsalling needed dependencies for compilation
sudo apt-get install libdb-dev libnspr4-dev libnss3-dev libical-dev libsqlite3-dev
sudo apt-get install bison intltool gnome-core-devel evolution-data-server-dev libcanberra-gtk-dev

sudo apt-get install libgtkhtml3.8-dev network-manager-dev libunique-dev libhal-dev

sudo apt-get install libgtkimageview-dev libpst-dev libnotify-dev

sudo apt-get install libmapi-dev samba4-dev libglib2.0-dev

tar fxj gtkhtml-3.28.2.tar.bz

cd gtkhtml-3.28.2
./configure
make 
sudo make install

tar fxj  evolution-mapi-0.28.2.tar.bz2
cd evolution-mapi-0.28.2
./configure
make
sudo make install
Start evolution via gnome menu.. and its works.;)

---

### Post by lipos on 2010-02-03
> checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for EVOLUTION_DATA_SERVER... yes
checking for LIBEDATASERVER... configure: error: Package requirements (libedataserver-1.2 >= 2.27.2) were not met:

No package 'libedataserver-1.2' found


I'm getting this after running it on 9.10
More libs need to be added, but all seems to be in the repositories.

---

### Post by pwebster25 on 2010-02-03
> **pavelchjen said:**
> tar fxj gtkhtml-3.28.2.tar.bz

Just needs a two at the end
```
tar fxj gtkhtml-3.28.2.tar.bz2
```

---

### Post by pwebster25 on 2010-02-03
> **lipos said:**
> I'm getting this after running it on 9.10
More libs need to be added, but all seems to be in the repositories.

Lipos-
I got those same errors.  In each case, I went into synaptic, found the package it was missing with dev following it and added it.  I then re-ran the same command and it kept getting a bit further, missing another package.  I finally got through without anything missing (I think).  I need to wait to open Evolution till I get to work.  We'll see how it works.

It has been pretty bad on the MAPI connection.  Missing lots of message bodies and/or chunks of messages that are blank.  All my calendar invites show up as code to my Windows-using colleagues.  :)

Pavelchjen-
If this works for me I'll let you know.  If so, thanks.

---

### Post by devinfriday on 2010-02-03
> **pavelchjen said:**
> I am running Ubuntu 9.10 karmic. And Evolution-mapi was not work for me from package repository. So I downloaded source code of newer exchange-mapi and GtkHTML compiled it and installed.

*snip

Start evolution via gnome menu.. and its works.;)

Even on my 9.10 ;) Sending/receive seems ok, evol doesn't sleep anymore when waiting too much for a new mail...
Now i'm praying the lord for a decent GAL support [-o<

---

### Post by posburn on 2010-02-04
So confused... I pulled down the latest version and compiled per the instructions above. It worked perfectly - send/receive, calendar, GAL - for about a day.

Now I'm getting the dreaded MAPI Network Error again. I changed nothing in my settings and now I can't authenticate.

This is frustrating. Any suggestions for where I should begin to troubleshoot?

---

### Post by devinfriday on 2010-02-08
> **devinfriday said:**
> Even on my 9.10 ;) Sending/receive seems ok, evol doesn't sleep anymore when waiting too much for a new mail...
Now i'm praying the lord for a decent GAL support [-o<

Turn back! The GAL still suffer from the same bug: when sending to multiple people @ different domains the mail will remains in the outbox.
Any advice?

---

### Post by MrSqueezles on 2010-02-19
I have a new problem.  After changing my Exchange password for the first time since setting up, Evolution now reliably locks my account.  Everything seems to work, but after about 10 minutes, my account is locked out.

---

### Post by niceshaman on 2010-03-29
Hi guys,

I have a problem. I can see only folders that have names in English, but all folders in different char sets (for e.g. in Russian) just not displayed at all. If you imagine that my "Inbox" has name in Russian, I can't see it at all :(

Does somebody know how to fix that, please?

Thanks.

---

### Post by jloflin on 2010-04-05
> **jmarks said:**
> 
Two other smaller issues:
1.  sent emails in the Outbox do not show to whom they were sent.
2. When I reviewed an email I sent in the Outbox, I found that it was presented in Japanese. (I typed it in English).  Accessing the same email via the web interface does, in fact, show it in Japanese, so I suspect that was how it was encoded and sent. A subsequent email I sent was in Englsh and encoded correctly.

Has anyone had these experiences, or can suggest ways to debug this? Worthy of bug reports?
thanks!

I have both of those issues.
To be more specific on #2, I can send and forward messages just fine, but when I reply to a message, it goes out in a font that looks japanese or chinese to me.

I just tried to copy an example into this message, but for some reason I can't do that. So I will attach an example.

Anybody know a fix?

---

### Post by mr_raider on 2010-05-18
Is this plugin workin in Lucid 10.04? i can't seem to find the option to create an exchange 2007 mapi account, but the evolution-mapi package is installed

---

### Post by hotani on 2010-05-27
I can set up an account with evolution-mapi in ubuntu 10.04 and it seems to work at first glance. However, there are a few showstopper issues:

[LIST=1]
[*] after Evolution has been running an hour or so, I can no longer get new messages and have to restart Evolution. The error reads "Error while refreshing folders"
[*] Replying to some HTML formatted messages results in the recepient receiving HTML code instead of a readable message. The message looks normal before sending.
[*] I can't read many HTML formatted messages, and there are no images in messages. "Load images" does not.
[/LIST]

So basically I can't reliably send or read e-mail. These bugs seem to exist in some form or another but are most often low priority.

---

### Post by dunnerz on 2010-06-09
> **hotani said:**
> I can set up an account with evolution-mapi in ubuntu 10.04 and it seems to work at first glance. However, there are a few showstopper issues:

[LIST=1]
[*] after Evolution has been running an hour or so, I can no longer get new messages and have to restart Evolution. The error reads "Error while refreshing folders"
[*] Replying to some HTML formatted messages results in the recepient receiving HTML code instead of a readable message. The message looks normal before sending.
[*] I can't read many HTML formatted messages, and there are no images in messages. "Load images" does not.
[/LIST]

So basically I can't reliably send or read e-mail. These bugs seem to exist in some form or another but are most often low priority.

ditto !

---

### Post by NoFear13X on 2010-10-09
I'm new to Ubuntu, as I've only been using it for about a week, but I gotta say, the lack of exchange support is the last straw in not moving over to Ubuntu completely.  I can blame other companies for things like Quickbooks not working or specific software I use not being compatible, but integrating with Exchange is something any smartphone or computer needs to be able to do.  This joke of a neverending forum post is example enough that things aren't moving along fast enough to be a complete replacement for Windows or MacOS.  It's just not there yet.

I have a combination of everyones issues starting with not being able to authenticate and ending with no longer being able to press the "forward" button in the wizard, and 3 hours later and a ton of forums and packages and downloads and sudo crap, I just have to give up.  It's not ready.  It's not even close...

Feel free to ignore this, but I had to vent.

---

### Post by dave100 on 2010-10-13
I used Evolution until our company moved to e2007 couple years back and the webdav(?) based interface broke (what MS was targeting I ques). After that only almost working solution has been davmail with Thunderbird.
There is also EWS based TB plugin which offers basic exchange calendaring features: [http://gitorious.org/lightning-exchange-provider/pages/Home](http://gitorious.org/lightning-exchange-provider/pages/Home). You might consider donation to speed development...
This exchange-mapi has been a sad joke for two years now. I know the lag of resources. (And maybe MS delivered some weak documents, after all, it does not want this to happen.) Also I think problem is depenencies between groups. Exchange-MAPI depends on libmapi from OpenChange and perhaps, working exchange-mapi is not the first priority for OpenChange group. Or not even the second... :-(

---

