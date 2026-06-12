---
title: "Mozilla Thunderbird won't work with Yahoo pop mail"
date: 2011-12-30
forum: Desktop Environments
---

### Post by jaime256 on 2011-12-30
I've configured thunderbird to fetch my yahoo mail so I can finally close that account since all it gets is more spam than anything.  I would like to back up the mail that's there, but thunderbird just tells me my password is wrong. I know it's correct since I can log into my mail through the web. I'm suing these links but still nothing. I notice they have some paid option now, which is more of a reason I want to finally close that account. I've attached the error as well. Any help is appreciated. If there's another back up options let me know. Thanks.
[http://help.yahoo.com//l/us/yahoo/mail/ymail/mailplus/pop/](http://help.yahoo.com//l/us/yahoo/mail/ymail/mailplus/pop/)
[http://help.yahoo.com/l/us/yahoo/mail/ymail/advanced/pop/pop-51.html](http://help.yahoo.com/l/us/yahoo/mail/ymail/advanced/pop/pop-51.html)

---

### Post by jaime256 on 2011-12-30
Well...I've been searching around for a client in windows that will let me download all the emails. Interestingly enough it looks like some companies like yahoo and Microsoft have gone a step backwards. Yahoo has that pop option only for paid accounts apparently, but I was able to download an open source client called zimbra that allowed me to get my emails. Now I just need to figure out how to make a backup so I can just store them since I need to check to make sure I got everything I need and I don't see any numbers of how many emails I have total like on yahoo to compare. 

With that said, microsoft now has something called live mail which is only included with a bunch of other software I don't care for and only supports this paid pop option. So I also tried thunderbird since I just wanted another download to see if I can check the numbers but the client on windows also doesn't allow me to do this. I just wished I could get my evolution working in Ubuntu as I prefer it and there's no windows version that I can find. Why do companies decide to go backwards is beyond me, but not being able to do the simple task of downloading my email for backup is just nuts. Needless to say once I'm sure I got all my emails I'll be closing my account there and never recommend yahoo again. So if anyone has any other options as to any other clients, please feel free to add them here. I need something  else for both Ubuntu and windows. I can't get kmail to work with pop  either but I'll have to go back and check that again.

---

### Post by lisati on 2011-12-30
To enable accessing your Yahoo mail (and that includes mail for ISPs that use Yahoo), you need to enable POP access on the mail options screen.

I'm surprised that MSN live expected you to download a whole lot of stuff, I've been using POP access from Ubuntu for a couple of years now, including on a recently opened Hotmail account, without the need for jumping through hoops to install stuff. It's possible to access their pop3 and smtp servers directly.

---

### Post by Frogs Hair on 2011-12-30
If this is up to date the pop server setting for Yahoo should be as follows . ```
 pop.mail.yahoo.com 
```

---

### Post by jaime256 on 2011-12-31
Thanks. I have but now when you are logged into yahoo, this is the only option you get when you go into the pop options. If I remember correctly I had set that up way back to allow me to use it though. I was trying to just install the mail client, but MS makes you download the whole live set of programs which I really didn't care for at the moment. Then it went to the live logon which I didn't want to do since I don't even remember what my account use to be. After closing and reopening the program I was able to use it and set that mail up, but on the very first screen I think they now tell you that you'll need a premium account if you want to use the pop mail. Yeah this is on the Microsoft client.


> **lisati said:**
> To enable accessing your Yahoo mail (and that includes mail for ISPs that use Yahoo), you need to enable POP access on the mail options screen.

I'm surprised that MSN live expected you to download a whole lot of stuff, I've been using POP access from Ubuntu for a couple of years now, including on a recently opened Hotmail account, without the need for jumping through hoops to install stuff. It's possible to access their pop3 and smtp servers directly.

---

### Post by jaime256 on 2011-12-31
Yes, this is still correct as you can see on the links I have on the first post. Thunderbird doesn't let me access the account. As I did mention, Zimbra did access the account under windows 7, but even under windows I still can't use thunderbird as I still get the same problem. It just won't fetch my mail. Two different machines and yes I have used pop before and have all the correct settings. I even tried the other port number suggested on the link in case my isp blocks some of the ports.

> **Frogs Hair said:**
> If this is up to date the pop server setting for Yahoo should be as follows . ```
 pop.mail.yahoo.com 
```

---

### Post by jaime256 on 2011-12-31
I used to use evolution with my yahoo and would still like to get evolution working if anyone can help me get that one going again. I just can't for the life of me get it to even install in Ubuntu 10.10. At this point I just want to try and get another client working on it so I'm sure I'll have my mail before I close that account. But I'll do that after I'm sure I got things backed up since I still need to sort though some of the junk mail there. I only skimmed through zimbra so I'm not sure where the backup option is on that one. Can't really find anything.

---

### Post by Frogs Hair on 2012-01-01
Evolution can be installed from the ubuntu software center . Just select install and enter your password when prompted . I am not familiar with zimbra at all , but I did find a number of methods for getting Yahoo mail to work in Tbird . I don't what you could do if your ISP blocks the needed ports though .

---

### Post by ottosykora on 2012-01-02
@jaime256

did you try some of the extensions for thunderbird which are made to read webmail?

---

### Post by Frogs Hair on 2012-01-02
You could give this a try .  [http://webmail.mozdev.org/](http://webmail.mozdev.org/)

---

### Post by jaime256 on 2012-01-02
Evolution would not installed a while back, I tried it today and It finally installed. It looks like a new version, but similar to the old one which is fine. Unfortunately I can't get this to work with yahoo pop either. I decided to un-install Thunderbird, I just don't like that interface.

> **Frogs Hair said:**
> Evolution can be installed from the ubuntu software center . Just select install and enter your password when prompted . I am not familiar with zimbra at all , but I did find a number of methods for getting Yahoo mail to work in Tbird . I don't what you could do if your ISP blocks the needed ports though .

---

### Post by jaime256 on 2012-01-02
I did try the mail extension but only found these and still wouldn't work with pop.


> **ottosykora said:**
> @jaime256

did you try some of the extensions for thunderbird which are made to read webmail?

---

### Post by jaime256 on 2012-01-02
I finally got fed up with this so I just went into my zinbra and checked to make sure all emails were there. There's an option to show by message so I could actually see the total number of emails. After I did this, I just went into my yahoo mail, manually deleted everything in it and went ahead and closed that email.
Here's the link to do so in case anyone else wants to get rid of them. Man I hate yahoo like th plague now.
[http://help.yahoo.com/kb/index?page=content&y=PROD_ACCT&locale=en_US&id=SLN2044&impressions=false](http://help.yahoo.com/kb/index?page=content&y=PROD_ACCT&locale=en_US&id=SLN2044&impressions=false)

Here's what they tell you after you close the account.
[http://info.yahoo.com/privacy/us/yahoo/datastorage/details.html](http://info.yahoo.com/privacy/us/yahoo/datastorage/details.html)

Thanks for trying guys. I think I may need to do this for my other old yahoo account since I noticed it's been getting spammed as well. I never used it much, but man they suck. Time to start the new year with a clean slate, sort of.

---

### Post by jaime256 on 2012-01-02
I do have a question? Does anyone know how to export from zimbra? I do an export for the whole account but I only get a tgz file that's 1kb or 2kb in size and I know this is not correct. There's no other option for the type of file to be exported...

I've also played with the live mail windows program and can't find the import to try and see if I can import to it. I'll try with evolution as I prefer it, but man I can't even get the correct file out. Any suggestions are appreciated. Thanks.


Okay I think I found another way to back up the mail in zimbra. Under preferences there's a "backups" option. I used this instead of the export and now I got a file that's 65,171kb after choosing the yahoo mail and unchecking the local folders, so at least I can back something up in case I mess things up with zimbra. Just remember where the file is.

I just backed this file up and it came out to 63.3megs I think it was. So I can rest a little better now. I'll have to go through that but at least I have a backup that I can play with now in evolution or whatever I guess. I won't know until I try messing with that, but I'll leave that for later.

---

### Post by jaime256 on 2012-01-05
I just want to update this a bit. I was just playing around with evolution trying to see if I could import my backup from zimbra to this and well, the short answer is no. I can't find a way to do this so you're stuck doing this in zimbra which sucks a bit but since I'm just reviewing stuff I'll take this over not being able to get my stuff from yahoo. Also one annoying thing about zimbra is that you can't change the setting for checking the account. I canceled the account and now the program nags me about the password being incorrect and theres no way to change this without verying the password first. So you're stuck with that unless you chose to check your mail manually when you first set that pop account up. Live and learn. I'll be very happy once I get rid of all my yahoo stuff.

---

### Post by lisati on 2012-01-05
> **jaime256 said:**
> Thanks. I have but now when you are logged into yahoo, this is the only option you get when you go into the pop options. If I remember correctly I had set that up way back to allow me to use it though. I was trying to just install the mail client, but MS makes you download the whole live set of programs which I really didn't care for at the moment. Then it went to the live logon which I didn't want to do since I don't even remember what my account use to be. After closing and reopening the program I was able to use it and set that mail up, but on the very first screen I think they now tell you that you'll need a premium account if you want to use the pop mail. Yeah this is on the Microsoft client.

I have been using POP access with Yahoo for several years now without paying a premium. Whether or not you pay for it can depend on a number of factors such as location. What I found was that when a price tag was put on POP access for yahoo.com accounts, I was still able to access yahoo.co.nz accounts by POP.

---

### Post by jaime256 on 2012-01-07
Well you're right, access had always worked fine, then they changed things and the programs also changed a bit, but I'm sure it has to do more with yahoo than anything else as you can still access pop with zimbra which is still a good thing. Unfortunately none of the other programs like evolution and thunderbird work for whatever reason. At least not on my end. Even when I installed the new windows mail program, it tells you that in order to use yahoo pop you need that paid pop or something to that effect. Your guess is as good as mine, I wished I had an answer but couldn't find one.

---

### Post by freebird54 on 2012-01-08
I don't know for sure how your Yahoo works, but in mine, under OPTIONS, there is an item for "forwarding and pop". I can just set it to forward mail, or to enable pop access.  I don't pay anything for that capability.  So far the mail shows up (Thunderbird for the moment) just fine.

Hope it helps :)

---

### Post by jaime256 on 2012-01-09
Thanks, I know exactly what you are talking about, but when I go to my pop options I don't get that for whatever reason. On post number 5 I put up a screenshot of what I got. No option for me to do anything anymore.

> **freebird54 said:**
> I don't know for sure how your Yahoo works, but in mine, under OPTIONS, there is an item for "forwarding and pop". I can just set it to forward mail, or to enable pop access.  I don't pay anything for that capability.  So far the mail shows up (Thunderbird for the moment) just fine.

Hope it helps :)

---

### Post by jmate24 on 2012-01-11
you have to pay in order to get that service from yahoo. my yahoo is the same as yours in post 5 if you want forwarding i suggest you use gmail.

---

### Post by jaime256 on 2012-01-11
I already cancelled that yahoo account which this thread is all about. I was just trying get help and help others trying to get their emails from there. I'm not sure when they changed that but it sucked either way.

> **jmate24 said:**
> you have to pay in order to get that service from yahoo. my yahoo is the same as yours in post 5 if you want forwarding i suggest you use gmail.

---

