---
title: "Can I access IE especific sites?"
date: 2012-07-18
forum: Desktop Environments
---

### Post by michaelbr on 2012-07-18
Greetings all:
I just installed Ubuntu 12.04 and would like to know how to setup Ubuntu/Firefox for access sites only accessible through IE (Hotmail and several China Mainland banks can only be accessed through IE) . I have the following setup:
- Ubuntu 12.04
- Firefox 14.0.1
- I'm sharing Ubuntu Firefox profile with XP

Thanks for your comment/suggestion
Michael

---

### Post by vasa1 on 2012-07-18
Yes and no.

It depends.

If a site is "IE-specific" by merely browser-sniffing, then spoofing the user agent may be enough.

If a site is "IE-specific" because it depends on stuff uniquely found on Windows, ActiveX ???, you have to use IE directly on Windows or, possibly, via Wine. My understanding is that Wine isn't set up to run IE9.

---

### Post by sammiev on 2012-07-18
Hotmail and banking sites work great here with Firefox.

---

### Post by michaelbr on 2012-07-19
> **vasa1 said:**
> Yes and no.

It depends.

If a site is "IE-specific" by merely browser-sniffing, then spoofing the user agent may be enough.

If a site is "IE-specific" because it depends on stuff uniquely found on Windows, ActiveX ???, you have to use IE directly on Windows or, possibly, via Wine. My understanding is that Wine isn't set up to run IE9.

Thanks for your reply, that's fine, I don't need IE9, IE7 should be enough, is there any other solution beside installing IE under Wine? I don't think it's Activex, some of the ASP features are not displayed in FF (such as confirmation code, etc.)

Thanks for your comment/suggestion
Michael

---

### Post by michaelbr on 2012-07-19
> **sammiev said:**
> Hotmail and banking sites work great here with Firefox.

I tried Hotmail using FF both in XP and Ubuntu, the 1st time I tried to login (I have set to clear cookies after closing FF), the user id & password fields showed up, after filling in the info and clicked Login, I got the following error:
The Windows Live Network is unavailable from this site for one of the following reasons:
and there's no id & password fields any longer (until I cleared MSN related cookies). In XP, if I switch to IETab, then those fields showed up again and I could use Hotmail through FF & IETab in XP.

What I have to do to access Hotmail from Ubuntu? I just did a fresh install and I'm pretty sure that I haven't mess up anything yet!!

You mentioned that bank sites can be accessed through FF, are you talking about Chinese bank sites? Most of Chinese bank sites use ASP and I could only access through IE or FF with IETab. I don't have problem accessing bank sites in US/TW/HK.

Thanks for your comment/suggestion
Michael

---

### Post by satish_j on 2012-07-19
You should first try the option suggested by vasa1.Switching User Agent from within FF allowed me to access certain websites that were previously not be accessed from base Firefox install.

---

### Post by michaelbr on 2012-07-19
> **satish_j said:**
> You should first try the option suggested by vasa1.Switching User Agent from within FF allowed me to access certain websites that were previously not be accessed from base Firefox install.
Thanks satish, how do I switch User Agent in FF? Could you please explain step by step?

Thanks

---

### Post by vasa1 on 2012-07-19
This should do it:
[https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/](https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/)

---

### Post by sammiev on 2012-07-19
I would love to know the addies that he has been having trouble with. Please post, I would love to try them myself.

---

### Post by rg4w on 2012-07-19
> **sammiev said:**
> I would love to know the addies that he has been having trouble with. Please post, I would love to try them myself.
Yes, I'm curious who's still writing browser-specific web apps in the 21st century.

---

### Post by michaelbr on 2012-07-19
> **vasa1 said:**
> This should do it:
[https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/](https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/)
Sorry vasa1, did not work, I added this addon and tried switch agent to IE7 and 8, both failed (showing the same error message).

---

### Post by michaelbr on 2012-07-19
> **sammiev said:**
> I would love to know the addies that he has been having trouble with. Please post, I would love to try them myself.
sammiev:
Until recently, I could get to [Hotmail]("http://login.live.com/login.srf?wa=wsignin1.0&rpsnv=11&ct=1269023404&rver=6.0.5285.0&wp=MBI&wreply=http:%2F%2Fco102w.col102.mail.live.com%2Fdefault.aspx&lc=1033&id=64855&mkt=en-us") by using just FF (without using IETab), but now I'm having trouble to login as described above. As for banking, the following [bank site]("https://vip.icbc.com.cn/icbc/perbank/index.jsp") only works with IETab (the 1st time you access it, it might ask you to install some security addons, it was long time ago, I don't remember any longer). I tried to access the site using FF 13.0.1 just before this post and the site said it only supports FF 10.0.X. As I said, this site is a Chinese bank site and it's in Chinese, unfortunately, I'm not sure if this will help you. The last time I tried to use FF without IETab, the site showed up normally, it just did not show the 3rd entry field, which is the user validation entry, with an empty field on the left and a code image on the right).

Thanks

---

### Post by vasa1 on 2012-07-19
> **rg4w said:**
> Yes, I'm curious who's still writing browser-specific web apps in the 21st century.

Some major international banks. Just search for recent hits with "browser sniffing banks".

---

### Post by sammiev on 2012-07-19
> **michaelbr said:**
> sammiev:
Until recently, I could get to [Hotmail]("http://login.live.com/login.srf?wa=wsignin1.0&rpsnv=11&ct=1269023404&rver=6.0.5285.0&wp=MBI&wreply=http:%2F%2Fco102w.col102.mail.live.com%2Fdefault.aspx&lc=1033&id=64855&mkt=en-us") by using just FF (without using IETab), but now I'm having trouble to login as described above. As for banking, the following [bank site]("https://vip.icbc.com.cn/icbc/perbank/index.jsp") only works with IETab (the 1st time you access it, it might ask you to install some security addons, it was long time ago, I don't remember any longer). I tried to access the site using FF 13.0.1 just before this post and the site said it only supports FF 10.0.X. As I said, this site is a Chinese bank site and it's in Chinese, unfortunately, I'm not sure if this will help you. The last time I tried to use FF without IETab, the site showed up normally, it just did not show the 3rd entry field, which is the user validation entry, with an empty field on the left and a code image on the right).

Thanks

Hi, Try this [Hotmail]("https://hotmail.com") addie and report back. I will look at the other shortly.

---

### Post by michaelbr on 2012-07-19
> **sammiev said:**
> Hi, Try this [Hotmail]("https://hotmail.com") addie and report back. I will look at the other shortly.
Sorry, did not work, it was redirected and I got the same error message.

Thanks

---

### Post by sammiev on 2012-07-19
> **michaelbr said:**
> Sorry, did not work, it was redirected and I got the same error message.

Thanks

I'm not sure of your laws there but I would suspect you are having addies blocked. Have you tried a proxy yet or a VPN with the country you are trying to accesses?

---

### Post by pjammr on 2012-07-19
Maybe I am in the wrong place. Using Xubuntu 12.04 and usually Firefox 14.  There is a  website I could easily access before but now I get different errors depending on how I try to log on   Chrome, Opera, IE in Wine.  A friend using my  id and password has no trouble using IE in Windows 7.  I tried  a Windows XP and still could not log on.  Today I even briefly considered installing Windows 7 because it is important for me to log on to this site

rightsourcer.com

Could this site need something only found in recent versions of Windows.  Is there something I need to add to my Xubuntu.  I also tried another Linux -Puppy and it is the same.  The site tech support is worthless, knows many users are having problems but can not seem to fix it.

Are there OS specific sites.  I tried firefox user agent.

---

### Post by michaelbr on 2012-07-19
> **pjammr said:**
> Maybe I am in the wrong place. Using Xubuntu 12.04 and usually Firefox 14.  There is a  website I could easily access before but now I get different errors depending on how I try to log on   Chrome, Opera, IE in Wine.  A friend using my  id and password has no trouble using IE in Windows 7.  I tried  a Windows XP and still could not log on.  Today I even briefly considered installing Windows 7 because it is important for me to log on to this site

rightsourcer.com

Could this site need something only found in recent versions of Windows.  Is there something I need to add to my Xubuntu.  I also tried another Linux -Puppy and it is the same.  The site tech support is worthless, knows many users are having problems but can not seem to fix it.

Are there OS specific sites.  I tried firefox user agent.
When I had problem with browser, I usually just use XP/FF/IETab, this solved so far my login/display problem with sites IE specific, maybe your problem is not OS related but browser related (in XP you were probably using older IE and in 7 you were using newer IE).

I just tried the above site in XP/FF/IETab, it seems it's been removed (does not exist any longer).

---

### Post by michaelbr on 2012-07-19
> **sammiev said:**
> I'm not sure of your laws there but I would suspect you are having addies blocked. Have you tried a proxy yet or a VPN with the country you are trying to accesses?
sammiev I don't think that's the case, if I tried to use XP/FF I got the error, but if I tried XP/FF/IETab, then I could login, so it's the same country/site/OS, the only difference is IETab in XP.

Thanks

---

### Post by danarock on 2012-07-21
I usually use chromium and IETab addon to access sites that would look better in the IE browser.

---

### Post by rg4w on 2012-07-21
Browser-specific public sites are antithetical to the nature of the Web, completely missing the point.

You might try sending this link to any of the bean counters that webmaster reports to:
[http://gs.statcounter.com/](http://gs.statcounter.com/)

There the manager will see that 67.69% of potential visitors are being prevented from using the company's site by the webmaster's decision to rely on IE-specific tags.

After sending the link, give it about two days for internal corrective action, then try the site again. ;)

---

