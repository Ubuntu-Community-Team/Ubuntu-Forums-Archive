---
title: "I Bet You Can't Solve This Problem"
date: 2006-08-04
forum: Desktop Environments
---

### Post by totfit on 2006-08-04
I am unable to login to my Bank of America account. I receive this error: "Your browser has sent an unrecognizeable query to our server". I can't login with any browser Opera, Firefox or Koqueror. Doesn't work in Gnome or KDE. If however I login in Ubuntu under my son's login everything works fine. Under my account I have deleted cookies, cache, and passwords for each browser and I still get this message. I am stumped. I would appreciate any thoughts/help that anyone might have. This is a big issue for me. 

Gregg

---

### Post by Akita on 2006-08-04
Not a clue, but you might want to cross-post this under networking too.

---

### Post by aysiu on 2006-08-04
Well, technically, B of A doesn't support Opera, Firefox, or Konqueror. From their website's [support section](http://www.bankofamerica.com/onlinebanking/index.cfm?template=faq_security#equipment): > **What kind of computer equipment and software do I need for Online Banking?**
You need a computer, modem, Internet access and one of the following recommended Internet browsers: Netscape 6.2 and higher, Microsoft Internet Explorer 5.0 and higher, or Safari 1.0 and higher (OS 10 only). You can use either a Macintosh or a Windows computer.

---

### Post by ardchoille on 2006-08-04
> **totfit said:**
> I am unable to login to my Bank of America account. I receive this error: "Your browser has sent an unrecognizeable query to our server". I can't login with any browser Opera, Firefox or Koqueror. Doesn't work in Gnome or KDE. If however I login in Ubuntu under my son's login everything works fine. Under my account I have deleted cookies, cache, and passwords for each browser and I still get this message. I am stumped. I would appreciate any thoughts/help that anyone might have. This is a big issue for me. 

Gregg

First of all, Bank of America changed the way it logs in users recently. They use a Site Key now. If you don't have a Site key, you'll need to sign up for it.

Secondly, Open Firefox. Click on Edit -> Preferences and go to the Advanced section, Security tab, and make sure all three checkboxes in the Protocol section are checked. Re-start Firefox and see if that helps.

firefox works fine at Bank of America, you just need the proper settings.

---

### Post by totfit on 2006-08-04
Technically Bank of America does not support Linux, but it works everywhere, but seemingly in my login for Ubuntu. I have all the security settings check in Firefox. All browsers worked up until a couple of weeks ago. Opera dropped first and later Firefox. Under my son's Ubuntu login on this computer I can access my BOA account with either Opera or Firefox. I can also access it if I use the Live CD for 6.06. My laptop works fine also with a similar configuration of my desktop. All browsers work. The problem is with my desktop, under my login. Yes, I have a site key also. It is from going to my login name to the site key where the error message occurs. Thanks for the input, but I am still at a dead end.

Gregg

---

### Post by ardchoille on 2006-08-04
Ok, the next thing I would check is: what are the differences in settings between your son's Firefox settings and yours? I would think, that if your son has access to it, but you don't, and both of you use the same box, then there is something different between his FF settings and yours (maybe some firefox extenion or plugin?). I would start investigating there. You can even use a diff app to check the differences between each file in his ~/.mozilla folder and yours.. if needed.

---

### Post by totfit on 2006-08-04
The only problem would be that it is not just Firefox specific, but with all other browsers also. Opera and Konqueror work with his login, but do not work with mine. I can login to another bank account from my login, just not bank of america. I will keep double checking settings.

Gregg

---

### Post by Paulo Wageck on 2006-08-04
use IE under WINDOWS under VMWARE under LINUX

---

### Post by PokerFacePenguin on 2006-08-04
Just throwing this out there...
Are you blocking javascript with noscript? using adblock or similiar?

---

### Post by jISh on 2006-08-04
> **Paulo Wageck said:**
> use IE under WINDOWS under VMWARE under LINUX
Use another operating system to accomplish a task such as logging into a web site? Seriously..

Sorry, it had to be said.

---

### Post by ardchoille on 2006-08-04
As PokerFacePenguin stated, blocking javascript would definitely keep you from logging into Bank of America. That has happened to me before. I am willing to bet it's an extension/plugin problem.

---

### Post by srunni on 2006-08-04
I doubt this will work, but you could try the User Agent Switcher plugin for Firefox. It lets you disguise yourself as IE/other browsers. You can find the extension at [https://addons.mozilla.org/firefox/59/](https://addons.mozilla.org/firefox/59/)

---

### Post by totfit on 2006-08-05
> **PokerFacePenguin said:**
> Just throwing this out there...
Are you blocking javascript with noscript? using adblock or similiar?
I was at first wondering if it might be a Java Script error, but I am not to my knowledge using any type of adblock and am not sure what noscript is even. I find the peculiar thing is that what I can't do: login with "any" browser under my Ubuntu login, I can do with every browser in my son's login or using the live cd or Ubuntu on my laptop. I'll poke around some more. I have already looked at Java settings and haven't noticed anything awry. Another peculiar thing is that this happened with Opera first, and then with Firefox later.

Thanks,
Gregg

---

### Post by msandersen on 2006-08-05
Ahh, the dreaded Bank of America worm... Joking! :)

---

### Post by totfit on 2006-08-05
Another oddity that I have discovered is that I can login to my Bank of America account by running either Opera or Firefox using sudo. Could there be a permissions problem? I can't see where it would be. There is a setting somewhere causing this mess, I just haven't a clue what it would be.

Thanks
Gregg

---

### Post by Patrick-Ruff on 2006-08-05
It seems odd that it would be, it could be possible that Bank Of America is trying to run such security app's, or something that I'm not aware of that is impossible to run on a linux computer without sudo... I don't nkow tho, its not safe to run a browser with sudo consistantly, thats just like less security then windows :P.


Good luck.

---

### Post by Patrick-Ruff on 2006-08-05
It seems odd that it would be, it could be possible that Bank Of America is trying to run such security app's, or something that I'm not aware of that is impossible to run on a linux computer without sudo... I don't nkow tho, its not safe to run a browser with sudo consistantly, thats just like less security then windows :P.


Good luck.

---

### Post by KFASheldon on 2006-08-05
Hmmm

Reading through this thread I think I will go with a Java problem, if all browsers fail to work for you then I would check your Java setup. Siplest way I can see sould be to re-install Java on your login, use Automatrix or something, I would guess all browsers use same Java engine if when you install and for some reaseon its messed up on your watch, just a thought might help.

Karl

---

### Post by ebash on 2006-08-05
Since you have tried all major browsers under your account everything seems to indicate that you have a problem with your environment variables.

On of the problems could be that you are using a proxy (check if http_proxy is defined) or that you'r not using the right version of java (check PATH, JAVA_HOME, CLASSPATH).

The best is to check the environment variables and check what are the differences.

Login as your son and do:
```
env | sort > /tmp/son.env
```

Then log back as your own user and do:
```
env | sort > /tmp/me.env
```

Check the differences on the environment:
```
diff /tmp/me.env /tmp/son.env
```

---

### Post by missmoondog on 2006-08-05
not exactly the same issue, but i can't login to my routers web pages interface using opera or konqueror. for a while, i couldn't login to it using ANY browser, but suddenly have been able to with firefox and epiphany.

never have been able to login to my banks website (5/3) using konqueror.

---

### Post by totfit on 2006-08-05
> **ebash said:**
> Since you have tried all major browsers under your account everything seems to indicate that you have a problem with your environment variables.

On of the problems could be that you are using a proxy (check if http_proxy is defined) or that you'r not using the right version of java (check PATH, JAVA_HOME, CLASSPATH).

The best is to check the environment variables and check what are the differences.

Login as your son and do:
```
env | sort > /tmp/son.env
```

Then log back as your own user and do:
```
env | sort > /tmp/me.env
```

Check the differences on the environment:
```
diff /tmp/me.env /tmp/son.env
```
This is what I get from checking differences, but can you interpret?

gregg@ubuntugregg:~$ diff /tmp/me.env /tmp/son.env
1,7c1,6
< COLORTERM=gnome-terminal
< DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-UxUke3SdXc,guid=5050d4442e515e3bcc731f5d6399e100
< DESKTOP_SESSION=gnome
< DESKTOP_STARTUP_ID=
< DISPLAY=:0.0
< GDMSESSION=gnome
< GDM_XSERVER_LOCATION=local
---
> COLORTERM=
> DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-RCRIjauEqN,guid=8999d444c4c0723612f90b57853bda00
> DESKTOP_SESSION=default
> DISPLAY=:20.0
> GDMSESSION=default
> GDM_XSERVER_LOCATION=flexi
9,10c8,9
< GNOME_KEYRING_SOCKET=/tmp/keyring-jad16x/socket
< GTK_RC_FILES=/etc/gtk/gtkrc:/home/gregg/.gtkrc-1.2-gnome2
---
> GNOME_KEYRING_SOCKET=/tmp/keyring-UvcQ4t/socket
> GTK_RC_FILES=/etc/gtk/gtkrc:/home/rad/.gtkrc-1.2-gnome2
12c11,13
< HOME=/home/gregg
---
> HOME=/home/rad
> KONSOLE_DCOP=DCOPRef(konsole-15279,konsole)
> KONSOLE_DCOP_SESSION=DCOPRef(konsole-15279,session-1)
17c18
< LOGNAME=gregg
---
> LOGNAME=rad
20,21c21,22
< PWD=/home/gregg
< SESSION_MANAGER=local/ubuntugregg:/tmp/.ICE-unix/5995
---
> PWD=/home/rad
> SESSION_MANAGER=local/ubuntugregg:/tmp/.ICE-unix/14842
24,25c25,26
< SSH_AGENT_PID=6046
< SSH_AUTH_SOCK=/tmp/ssh-PbqqTK5995/agent.5995
---
> SSH_AGENT_PID=14892
> SSH_AUTH_SOCK=/tmp/ssh-Ivrlj14842/agent.14842
27,28c28,29
< USER=gregg
< USERNAME=gregg
---
> USERNAME=rad
> USER=rad
30,31c31,32
< WINDOWID=25165917
< XAUTHORITY=/tmp/.gdmM5y1Q7
---
> WINDOWID=35651591
> XAUTHORITY=/home/rad/.Xauthority
gregg@ubuntugregg:~$
gregg@ubuntugregg:~$

Thanks,
Gregg

PS. I have found that I can login to my BOA account with either Firefox or Opera using sudo.

---

### Post by ebash on 2006-08-05
I have looked fast through your environment variables and I can't see the problem. :-( 

The problem might not be related to the environment variables after all.

You must have configured something wrong in both firefox and opera under your account. Because the other users: your soon and root (when you sudo), don't seem to have problems. Do you have cookies and javascript enabled?

Try the following: close all instances of firefox, rename the folder .mozilla, restart firefox and go to your bank account. If it works then compare the new .mozilla folder with the old one.

PS: I'm about to leave for a week without any internet access. Thus, I won't be able to help you for a week. I hope that you managed to get your bank account access fixed :D

---

### Post by ardchoille on 2006-08-05
> **KFASheldon said:**
> Hmmm

Reading through this thread I think I will go with a Java problem, if all browsers fail to work for you then I would check your Java setup. Siplest way I can see sould be to re-install Java on your login, use Automatrix or something, I would guess all browsers use same Java engine if when you install and for some reaseon its messed up on your watch, just a thought might help.

Karl

I have not installed any java stuff at all and I can log into Bank of America using Firefox. I don't think it's a java issue.

---

### Post by totfit on 2006-08-05
> **ebash said:**
> I have looked fast through your environment variables and I can't see the problem. :-( 

The problem might not be related to the environment variables after all.

You must have configured something wrong in both firefox and opera under your account. Because the other users: your soon and root (when you sudo), don't seem to have problems. Do you have cookies and javascript enabled?

Try the following: close all instances of firefox, rename the folder .mozilla, restart firefox and go to your bank account. If it works then compare the new .mozilla folder with the old one.

PS: I'm about to leave for a week without any internet access. Thus, I won't be able to help you for a week. I hope that you managed to get your bank account access fixed :D
I tried this which gives me a totally new identity for Firefox, correct? Still a no go. It has to be a setting in my Ubuntu idenity. I just don't know where or what it would be. I keep thinking permissions possibly, but don't really know where to look. Thanks for the suggestion.

---

### Post by PokerFacePenguin on 2006-08-05
> **totfit said:**
> I tried this which gives me a totally new identity for Firefox, correct? Still a no go. It has to be a setting in my Ubuntu idenity. I just don't know where or what it would be. I keep thinking permissions possibly, but don't really know where to look. Thanks for the suggestion.

Hmm, it could be something with permissions...having you been chmod/chgrp happy in the home directory lately?  Check the permissions against what the permissions that your son's account has for the .mozilla directory and below it....do they look similiar?

I would save my settings as a backup and chmod/chgrp that .mozilla directory(and everything below it) to 777 (world writable) to see if that will do anything at all.  At least that could rule out permissions.

---

### Post by totfit on 2006-08-06
> **PokerFacePenguin said:**
> Hmm, it could be something with permissions...having you been chmod/chgrp happy in the home directory lately?  Check the permissions against what the permissions that your son's account has for the .mozilla directory and below it....do they look similiar?

I would save my settings as a backup and chmod/chgrp that .mozilla directory(and everything below it) to 777 (world writable) to see if that will do anything at all.  At least that could rule out permissions.
Just changed all permissions to world writable and still a no go. I am just about at the point your signature states. :-)

---

### Post by PokerFacePenguin on 2006-08-06
> **totfit said:**
> Just changed all permissions to world writable and still a no go. I am just about at the point your signature states. :-)

Sounds like you have ruled out permissions on that .mozilla directory...

The thing that sounds too weird is that you can sudo and get it done.  That sounds like permissions to me....it is just a matter of finding the right directory.  Perhaps it is the java version or the java directory (and associated permissions) that you should focus attention on.  Also, you might take a look in your logs.

---

### Post by totfit on 2006-08-06
I have been messing with java permissions also. I will probably keep tinkering till I "break" something and have to clean install. That will probably for sure fix the problem once and for all.:-k 

Gregg

---

### Post by darell_m on 2007-06-07
This a very old tread but I cannot log in my bank as is says I need IE this and that or nectscape this or that.

I have really looked at all threads - do I need to install IE uner wine - that sucks - use Konqueror why another program - I use newest of firefox - but maybe have to do more.  Thanks for any advice - this is not a https site only http

thanks for help:p

---

### Post by totfit on 2007-06-07
> **darell_m said:**
> This a very old tread but I cannot log in my bank as is says I need IE this and that or nectscape this or that.

I have really looked at all threads - do I need to install IE uner wine - that sucks - use Konqueror why another program - I use newest of firefox - but maybe have to do more.  Thanks for any advice - this is not a https site only http

thanks for help:p

What bank and what error message are you getting? I can't imagine there being any bank in the world now that you can't log in with Firefox. I was the one that started this original thread and never quite figured out what the problem was with that particular identity, but I have since reworked everything and am logging in just fine. What banks typically say is that they don't support other browsers, but you can still use them. More details would be helpful. 

Gregg

---

### Post by darell_m on 2007-06-07
> **darell_m said:**
> This a very old tread but I cannot log in my bank as is says I need IE this and that or nectscape this or that.
 
I have really looked at all threads - do I need to install IE uner wine - that sucks - use Konqueror why another program - I use newest of firefox - but maybe have to do more.  Thanks for any advice - this is not a https site only http
 
thanks for help:p
 
 
 
Hey guys _ I spent more time searching and loaded SWITCHER  from available downloads and go to FireFox tools and click switcher and chose IE 7 or whatever works and it loads . Then make whatever works your default.
 
 
:):):):)Walla - works great

---

### Post by gjtoth on 2007-06-07
You can try making a new user, logging in as him and then try logging on.  Might be something in your user settings.

Just a thought.

---

### Post by llamakc on 2007-06-07
One of my credit cards web interface REFUSES to work for me completely with Linux/Firefox. That's why I use IEs4Linux [http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page) which works perfectly.

---

### Post by darell_m on 2007-06-07
> **darell_m said:**
> Hey guys _ I spent more time searching and loaded SWITCHER  from available downloads and go to FireFox tools and click switcher and chose IE 7 or whatever works and it loads . Then make whatever works your default.
 
 
:):):):)Walla - works great
 
Switcher default setting????
 
Except I failed to make IE 7 my default so each time must go to tools switcher and choose I.E 7 to login to bank site - any idea how to change default in switcher as seems simple but cannot figure it out.  Any ideas? 
 
But does work great for logging into secure sites that seem to work only under MS - so give a try an let us know. but? I would really not want to go and extra click or two if I don't have to? See avatar and 65 yo, so every click is more energy I don't want to use HA!

 
 
 
:p

---

### Post by the_tazinator on 2007-06-07
Try copying his firefox profile to your user account and see if it works. Look in /home/<user>/.mozilla/firefox. Start firefox with the profile manager (firefox -ProfileManager) and create a new profile. Copy the files in his /home/<user>/.mozilla/firefox/****.default into the new profile you created. Restart Firefox with 'firefox -ProfileManager' again and select your new account. This will let you know if it is a firefox issue or a user account issue.

...or try ies4linux ([http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page))

---

### Post by darell_m on 2007-06-08
> **totfit said:**
> What bank and what error message are you getting? I can't imagine there being any bank in the world now that you can't log in with Firefox. I was the one that started this original thread and never quite figured out what the problem was with that particular identity, but I have since reworked everything and am logging in just fine. What banks typically say is that they don't support other browsers, but you can still use them. More details would be helpful. 
 
Gregg



Sorry not to reply earlier - I am in Cairo Egypt with HSBC and here is error as copy/paste from bank login site/




[FONT=Arial,][SIZE=2]"For Windows PC :

‘To access internet banking, please use:

Netscapeversion 4.72 or above (version 6.x currently not supported), orInternet Explorer version 5.0 or above - with 128-bit encryption.’"[/SIZE][/FONT]


[FONT=Arial,][SIZE=2]Switcher works and not much hassle. Also tried ies4linux but no luck with that install (maybe did some error? on install as others have good success)[/SIZE][/FONT]


[FONT=Arial,][SIZE=2]BUT, Firefox should work directly as mentioned?[/SIZE][/FONT]


[FONT=Arial,][SIZE=2]Thanks Greg and all[/SIZE][/FONT]


[FONT=Arial,][SIZE=2]Darell:confused:
[/SIZE][/FONT]

---

### Post by totfit on 2007-06-08
I would assume that Firefox should work, but if it doesn't and switcher makes it work I would continue to use that if I were you. Just curious, have you tried Opera or other browsers?

Gregg

---

### Post by darell_m on 2007-06-09
> **totfit said:**
> I would assume that Firefox should work, but if it doesn't and switcher makes it work I would continue to use that if I were you. Just curious, have you tried Opera or other browsers?
 
Gregg
 
 
 
Gregg et al,
I don't like to give (but still no joy except using Switcher) but so others will know. I installed Automatix and installed Swiftfox and all plugins, but still get same login error to bank. PS firefox works fine under XP (I have dual boot). Also installed Opera and no joy. Maybe is something in my FF setup, which is likely well beyond noob level??
 
 
 
 
just for info
 
 
 
Darell

---

### Post by totfit on 2007-06-09
> **darell_m said:**
> Gregg et al,
I don't like to give (but still no joy except using Switcher) but so others will know. I installed Automatix and installed Swiftfox and all plugins, but still get same login error to bank. PS firefox works fine under XP (I have dual boot). Also installed Opera and no joy. Maybe is something in my FF setup, which is likely well beyond noob level??
 
 
 
 
just for info
 
 
 
Darell

You probably would have the same behaviour with Swiftfox, since it is essentialy the Firefox with your same settings, but tweaked to be a bit quicker. Something you might try and do just out of curiosity is run Firefox or Swiftfox and root or under another identity and see what happens. I mentioned that I never really solved my problem with the login at Bank of America. I just started over again with a new install and didn't have the problem. I still think it was somewhere in permissions or security settings, but tried every combination I could think of and had a lot of suggestions from here, but still could not find the solution. I would be curious if you could do it with root or another identity. It could be a very similar problem, except that switcher works for you and nothing would for me other than root or an different identity. 

Gregg

---

