---
title: "[SOLVED] Hotmail not working in Firefox"
date: 2008-11-05
forum: Desktop Environments
---

### Post by alexham on 2008-11-05
When I click on "New", email page downloads but the formatting toolbar and the text area are greyed out and I cannot write any text. I can insert the recipient's address and the subject title, but that is all.

By the way, the Firefox preferences>privacy is set to accept cookies from sites and third parties, so that is not the cause.

Many thanks,

Alex

---

### Post by ram130 on 2008-11-06
For me it is different. When i sign in to hotmail and click inbox it freezes for 5min then it comes up, but when i click on a message it does not doing anything. Y?

---

### Post by darkvampire on 2008-11-06
This is probably due to Mircosoft trying to block out Linux - even though this is illegal. :mad:
I did have the same problem a while back with 7.04
I installed Opera and that did the trick :wink:

**Opera**
[http://www.opera.com/download/linux/]("http://www.opera.com/download/linux/")

---

### Post by darkvampire on 2008-11-06
Also; I forgot to add - make sure that you are using "Classic" and not the "Full" live hotmail.
"Full" is only recommended with Windows + IE/Firefox.

---

### Post by Mourf on 2008-11-06
Hello, I've the same problem.  I can't write in the main body text in hotmail... Searched a lot to switch to classic hotmail but it seems like you can't get back once you're on the new live hotmail (and right now, everyone got switched to the new hotmail).

Does anyone have a clue?
Thanks
Alex

---

### Post by blazerw on 2008-11-06
Hotmail has always been less than stellar. I only use it for spam. The current workaround for me is to use the mobile site: [http://mobile.live.com/hm](http://mobile.live.com/hm)
In my opinion, it's simpler, faster and easier.

---

### Post by darkvampire on 2008-11-06
> **blazerw said:**
> I only use it for spam.


You send spam? ¬¬

---

### Post by darkvampire on 2008-11-06
> **Mourf said:**
> Hello, I've the same problem.  I can't write in the main body text in hotmail... Searched a lot to switch to classic hotmail but it seems like you can't get back once you're on the new live hotmail (and right now, everyone got switched to the new hotmail).

Does anyone have a clue?
Thanks
Alex

The new hotmail doesn't give you any real extra features other than the viewing panel; which really just slows your internet down. Your not missing anything by being in classic mode. You can switch back at any time.
I strongly recommend Opera. I had the same problem in 7.04 and ended up using Firefox for browsing and Opera for Email.

See the link in my first post.

---

### Post by alexeix on 2008-11-06
> **darkvampire said:**
> This is probably due to Mircosoft trying to block out Linux - even though this is illegal. :mad:
I did have the same problem a while back with 7.04
I installed Opera and that did the trick :wink:

**Opera**
[http://www.opera.com/download/linux/]("http://www.opera.com/download/linux/")


I've got the same problem too, however, I highly doubt that there's any dubious reason for this issue, such as Microsoft wanting to "block out" Linux. :roll:
More likely is that the redesigned Hotmail wasn't tested on Linux - which wouldn't be totally unexpected.
I don't know, but it's possible that this issue happens on the Windows version of Firefox (latest version) as well - is anyone able to check?

I'm sure a fix will be along, once people report the problem - I'm going to do that right now.

---

### Post by mister_p_1998 on 2008-11-07
I repeatedly have a similar problem with Gmail, it says my password is wrong when I know its not, it seems to be a Firefox problem as it does it in XP as well.

Steve

---

### Post by celticbhoy on 2008-11-07
enter about:config in address bar & change vendor from Ubuntu to Firefox

---

### Post by blazerw on 2008-11-07
Just to clarify, the preference name is "general.useragent.vendor". You can use the Filter and just enter "vendor" to find it quickly. Double click on the "general.useragent.vendor" line and replace Ubuntu with Firefox. Then, when you're done with Hotmail, change it back. Give Ubuntu credit when you visit other sites.

---

### Post by darkvampire on 2008-11-07
> **alexeix said:**
> I've got the same problem too, however, I highly doubt that there's any dubious reason for this issue, such as Microsoft wanting to "block out" Linux. :roll:
More likely is that the redesigned Hotmail wasn't tested on Linux - which wouldn't be totally unexpected.
I don't know, but it's possible that this issue happens on the Windows version of Firefox (latest version) as well - is anyone able to check?

I'm sure a fix will be along, once people report the problem - I'm going to do that right now.

[http://navetz.com/view.php?id=109](http://navetz.com/view.php?id=109)

(:

And my Firefox is fine in XP.

---

### Post by alexham on 2008-11-08
Hi, Guys,

I may have a solution.

Open Firefox and click on File>New Tab and type "about:config" without inverted commas, then confirm that you want to access configuration. When the list appears locate the entry general.useragent.vendor and change the value from Ubuntu to Firefox, then save and exit.

Let me know if it works for you.

Best Regards,

Alex

---

### Post by alexeix on 2008-11-08
> **darkvampire said:**
> [http://navetz.com/view.php?id=109](http://navetz.com/view.php?id=109)

(:

And my Firefox is fine in XP.

If this is a problem for Gmail as well (as mentioned by mister_p_1998), that kind of suggests that both Gmail and Hotmail are not tested on the Linux platform.

I know for a fact that the new Hotmail works on OSX, so it seems that only Windows and OSX are supported 'out of the box' (although there seem to be workarounds for the problem).

If this was about 'blocking' users of non-Windows operating systems, why not block OSX as well?

Anyway, thanks to everyone who's suggested the workaround!

---

### Post by Dennis N on 2008-11-09
I find Firefox 3.0.3 to work fine in gmail. As with the other posters, it does not work in hotmail (the text editor does not work, so I cannot send any mail). However, my laptop with Firefox 2 and Ubuntu works fine with both hotmail and gmail.

Edit: Further checking shows Firefox 2.0.0.17 also has problems. I can reply to messages but when creating a new one, even though typing the message is possible, the Subject line and To line are not accessible. The To button works to allow selection from contact list, however.

Edit 2: Solution that worked: Installed User agent switcher in Firefox 2.0.0.17. However, the Default Setting and IE setting did not work for me. I needed to created a new user agent with the ADD button (User Agent Switcher > Options > User Agents > Add) and used the information supplied in the following post to create the new User Agent Info: 

[http://ubuntuforums.org/showpost.php?p=6128646&postcount=13](http://ubuntuforums.org/showpost.php?p=6128646&postcount=13)

Tested, and now everything I tried was again functional.

---

### Post by ryry46d9 on 2008-11-09
this problem is related to firefiox 3.0.3 as any thing before that works fine

---

### Post by netsabes19 on 2008-11-09
Hello,

I've had got the same problem on Hardy Heron.

the solution exposed upper, consisting in replacing "Ubuntu" by "Firefox", works fine. But it's a bit tiresome to do it every time you have to answer a mail.

Is there anyway (a script for example) to make it automatically changed either by a button in Firefox, or when it starts ?

Regards.

SD.

PS : It's scandalous !

---

### Post by jflaker on 2008-11-09
It  works for me if I use the Firefox Add-on "User Agent Switcher"

If you choose IE/Vista, it works so I can get to the inbox, but can't open the email.

Just mark this one as another attempt from Microsoft to jail you to their products...

Microsoft breaks Hotmail for Linux users
[http://linux-watch.com/news/NS6023147333.html](http://linux-watch.com/news/NS6023147333.html)

---

### Post by ronnielsen1 on 2008-11-09
Have you tried to email today?

---

### Post by netsabes19 on 2008-11-09
ya.

The same problem occurs.

---

### Post by netsabes19 on 2008-11-09
And the add-on UserAgentSwitcher doesn't change anything for me.

It's worse : with UAS, I can't READ my emails !

And when I restart Firefox, all the different keys are initialized to their default values. So I forget "Firefox" and retrieve "Ubuntu".

SD.

---

### Post by ronnielsen1 on 2008-11-09
Maybe it's part of their plan

> to deliver interoperability and intellectual property (IP) peace of mind for organisations operating mixed-source IT environments.

---

### Post by munchkinmunchkin on 2008-11-10
I have the same problem, I can't reply to any Hotmail emails, the text window is greyed out and some of the buttons don't work. I tried the User-agent switcher, but to no avail. Looks like I will be ditching MicroSoft completely, and getting a GoogleMail account.

---

### Post by ronnielsen1 on 2008-11-11
Appears Opera works no problem

---

### Post by alexeix on 2008-11-11
This could of course be a bug, since I can't find anywhere that states which operating systems are supported.

Has anyone raised it with support?

---

### Post by thunderbirdje on 2008-11-11
Same problem here (for some weeks).

Didn't try the about:config because I do find Ubuntu deserve credits, I rather kick out hotmail than :-)

But it is maybe interesting to know, when I sign in I get a 'warning' which is totally incorrect because **I am using Mozilla Firefox (3.0.03)**

> Upgrade your web browser
We recommend that you upgrade your web browser so you can get the most out of Windows Live Hotmail. Upgrading should only take a few minutes. To get started, choose one of the browsers below:

    * Microsoft Internet Explorer
    * Mozilla Firefox
    * Apple Safari

If you don't want to upgrade right now you can still continue to Windows Live Hotmail, but some parts of it may not work and it may not be displayed properly.
Got a mobile device? Check your e-mail by going to [http://mobile.live.com/hm](http://mobile.live.com/hm).


I guess somewhere hotmail is detecting the wrong browser or version. 

I also did try to write a new email in 'plain text' instead of 'rich HTML', didn't work too.

---

### Post by rafttrip on 2008-11-12
Maybe I am missing something....but is this problem solved or not?

I can't seem to get hotmail working in Firefox 3 or Opera.

---

### Post by ronnielsen1 on 2008-11-12
> I can't seem to get hotmail working in Firefox 3 or Opera. 	

I can't email from firefox. I can email in hotmail from Opera. Do you have the latest Opera installed? I have Opera 9.62

---

### Post by on5sl on 2008-11-12
edit: I didn't read that well apparently...i was changing the wrong setting.
thx guys!
still i think this is very big showstopper for new ubuntu users...

---

### Post by neon100 on 2008-11-14
user agent solution worked perfectly fine. But is this really a complete evidence to file a lawsuit?

---

### Post by rafttrip on 2008-11-17
I have opera 9.62 installed...and it seams to work today. Not sure what the problem was before sory.

---

### Post by alexeix on 2008-11-20
So the latest update to Firefox seems to have resolved this problem.

Or the update may just be a coincidence.

Regardless, I can now type messages from Hotmail using Firefox.

Happy days. :)

---

