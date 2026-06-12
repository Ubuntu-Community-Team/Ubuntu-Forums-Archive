---
title: "Pidgin, Kopete not working for any service"
date: 2009-06-18
forum: General Help
---

### Post by tomhanna on 2009-06-18
Since this afternoon I can't get Pidgin or Kopete to connect to any IM service (Yahoo, MSN, AIM or Google Talk) on two different computers.  One of them is a dual boot with Windows XP and is able to connect to all the IM services running under Windows.

Ubuntu release 8.04 (hardy)
Kernel Linux 2.6.24-24-generic
GNOME 2.22.3

When I first noticed the problem, I checked the Pidgin site, updated to the latest version and ran the update manager on both computers.  That didn't help, so I installed and tried Kopete and it won't connect on either computer.

Obviously not a firewall problem (working fine under Microsoft's product) and not the Yahoo problem noted elsewhere (this is affecting all messenger services not just Yahoo) and also not just a problem with Pidgin (it's affecting other programs).

---

### Post by Villiam on 2009-06-18
Since its affecting other programs as well (other than Pidgin) it must be related to either your network configurations or your os. There is a thread where pidgin not connecting issues are discussed. You can check it over here: [http://ubuntuforums.org/archive/index.php/t-587907.html](http://ubuntuforums.org/archive/index.php/t-587907.html)

[ubuntu]("http://www.linux-archive.org/ubuntu-user/")

---

### Post by james.wilde on 2009-06-19
I'm not sure on that, Villiam.  I'm having the same problem with Pidgin since last night.  Haven't tried anything else, but I have tried from a windows instance running under Sun virtual box, and it works.


My experience says it's Pidgin.  I've tried disabling and re-enabling my accounts without result.  I've also tried uninstalling and re-installing pidgin.

I have also tried from my wife's Windows box, which sits on the same network.  She can send and I can reply, and I can initiate a conversation.  It appears to be the symbol in the system box and the buddy list which permanently shows Pidgin as connecting.

//James

---

### Post by easybeat on 2009-06-19
Hi

same problem for me on ubuntu 8.10 and pidgin 2.5.5. Not able to login!

Hopefully we will get a solution for this soon.

Thanks

easybeat

---

### Post by Mihai Stefan on 2009-06-19
That happened to me too. Neither Kopete nor Pidgin can connect to my Yahoo account since yesterday afternoon.

---

### Post by Deach on 2009-06-19
Or perhaps it's something yahoo has done since pidgin, kopete, adium (mac) aren't connecting either??  On kopete and pidgin over riding the default server with "66.163.181.172" has worked here. I have no idea about the OP not connecting to any IM protocol though, google talk was still working here.  It's the only other one I use.  Good luck.

---

### Post by hazica on 2009-06-19
> **Deach said:**
> Or perhaps it's something yahoo has done since pidgin, kopete, adium (mac) aren't connecting either??  On kopete and pidgin over riding the default server with "66.163.181.172" has worked here. I have no idea about the OP not connecting to any IM protocol though, google talk was still working here.  It's the only other one I use.  Good luck.


Just wanted to say I've had the same problem - Kopete and Pidgin unable to login to Yahoo - and overriding the default server with 66.163.181.172 brought me back online. So, thanks Deach!

---

### Post by Deach on 2009-06-19
You're welcome.  Glad to help.

---

### Post by BOZG on 2009-06-19
Where exactly do you override the default server?  The only server options I can find for Yahoo is under the check box for Yahoo Japan settings.  Do you change it there?

---

### Post by Deach on 2009-06-19
Not using pidgin for a while it seems to me though "accounts>edit account> advanced> pager it's called the one at the top.

Edit:
Yes it's there.  I grabbed pidgin real quick and changed the pager setting and I can log on now to yahoo......

---

### Post by tonyric on 2009-06-19
Yup change the pager from yahoo.com to 66.163.181.172

---

### Post by BOZG on 2009-06-19
Thanks a lot.  I misread that page and assumed that all the settings there were related to Yahoo Japan.

---

### Post by james.wilde on 2009-06-19
Damn!  Changed the MSN server by mistake.  Can someone give me the default MSN server.

---

### Post by nonolemono on 2009-06-19
messenger.hotmail.com

---

### Post by Therion on 2009-06-19
Why this is happening:

[http://www.ymessengerblog.com/blog/2009/06/09/we%E2%80%99re-retiring-versions-60-to-75/](http://www.ymessengerblog.com/blog/2009/06/09/we%E2%80%99re-retiring-versions-60-to-75/)

The workaround (until there's an update):

[http://ubuntuforums.org/showpost.php?p=7483375&postcount=12](http://ubuntuforums.org/showpost.php?p=7483375&postcount=12)

---

### Post by blueshiftoverwatch on 2009-06-24
Both AIM and Yahoo aren't working for me. I tried the Yahoo fix but it's saying that my username is invalid when I just used it a week ago.

Also, what's the deal with AIM not working? So far I've only read why Yahoo isn't working.

---

### Post by ajopaul on 2009-07-12
for kopete with yahoo this server seems to work fine. cn.scs.msg.yahoo.com

---

