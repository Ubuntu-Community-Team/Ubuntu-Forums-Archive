---
title: "Which UK broadband provider?"
date: 2009-03-10
forum: General Help
---

### Post by peter1608 on 2009-03-10
Hello

I’m trying to restart my exploration of Ubuntu from scratch, after an 18 month hiatus for personal reasons.   I currently have a CD of version 8.10 (from a magazine cover), which I have run as a live version but not installed.

My main query concerns internet connectivity.   I live in the UK and am searching for a broadband provider whose offerings are compatible with Ubuntu – but none of the providers’ mention linux compatibility at all.

On other criteria, my current first choice is the Post Office Home Phone and Broadband.  Has anyone managed to connect to this service with Ubuntu, and are there any step by step instructions out there?  Or can anyone recommend an alternative provider, with easy to use instructions for the novice?

Thanks in advance

Peter

---

### Post by blazemore on 2009-03-10
Linux compatibility isn't an issue.
The modem/router connects to the Internet. Your PC then connects to the modem/router. THerefore, it's the ROUTER'S Linux compatibility you need to worry about, and all (or most) are find.

I'd reccommend a cable service such as Virgin Media, because they give you a cable modem and you can choose your own router (if any).

---

### Post by shadowfirebird on 2009-03-10
Okay, my 10p.  Listing Linux compatibility really means that the ISP is willing to *support* Linux, more than the fact that Linux users will be able to connect, I think.  

Presumably there is some small risk that the ISP will do something weird that locks the Linux user out, but I suspect that it is a very small one.  (Perhaps someone more knowledgable about networking than I can quantify the risk.)  

For certain you should make sure that the ISP lists the IP addresses of their DNS servers rather than telling you to accept the default, and ideally there should be plenty of information regarding manually setting up connection settings.  If you take this route it might also be an idea to keep one Windows PC going so that you can pretend you use that if you have to call support.

My ISP?  I'm with Talktalk.  It's horribly slow and I'm sure the support quality is dire.  But I'm paying a pittance for the service, and I even get free calls to the US...

---

### Post by ssam on 2009-03-10
i am using [UKFSN]("http://www.ukfsn.org/"). they are not the cheapest, but they are good.
* profits go towards freesoftware
* real bandwidth limits (not 'unlimited, fair usage policy applies')
* no 12 month lock in
* no phorm
* are able to give me 8Mb, where tiscali could only manage 2Mb (and took weeks of excuses and lies to even give me that)
* good problem reporting/admitting [http://noc.enta.net/](http://noc.enta.net/)

they had some bandwidth/capacity issues towards the end of last year, but these seem to be all resolved now.

---

### Post by mr_git on 2009-03-10
Hi Peter,

Whilst few broadband providers advertise support for linux, it shouldn't really matter as long as you can connect to your broadband modem from your linux machine.

If you're planning to use a wired connection, try and make sure the modem has an ethernet connection (as opposed to USB only). Ethernet doesn't care what operating system you're using (as long as you have an ethernet network card in your machine which is supported in linux - which pretty much all but the most obscure are).

If you're planning on using wireless, you'll obviously need to ensure that your wireless hardware is supported in ubuntu; which you should be able to test running the live CD (does network manager show any wireless options? if wireless is working it may pick up your neighbours' wireless networks, for example)

It sounds like you're planning on going with ADSL (which uses your phone line, rather than a cable provider like Virgin Media). If you're planning on using modem / router hardware provided by the ISP, you'd just need to make sure that whatever they're going to give you has at least one ethernet port for wired connections.

Alternatively, you could use your own modem / router hardware. I've got limited experience of ADSL, but I have set up third party ADSL modem / wireless router combos (as opposed to ones provided by the ISP) to work with ADSL connections without any trouble.

You may not get much help from the ISP's technical support if you use your own modem / router hardware and linux, but you shouldn't really need it - although it might help if you can boot a machine into an operating system they do support in order to get the connection set up in first place.

If they can help you get a machine running windows connected to their service via an ethernet connection to the modem, you should be able to boot into ubuntu with the same wires etc... plugged in, and it should 'just work'.

Most wireless routers are administered via a web-based interface anyway, so you can usually set up whatever options you need from your browser in linux (I have seen a few rubbish web interfaces that don't work well in browsers other than Internet Explorer, but I think you'd be unlucky to come across one like that nowadays - the problem's not insurmountable anyway with something like ies4linux).

Hope that helps - don't know if that's the sort of information you were looking for - let me know if I can clarify anything I've said there.

---

### Post by mixmaster on 2009-03-10
For what it is worth I use a netgear wired/wireless router.  The router is administered via a web interface which works fine with firefox.  There is a windows/mac setup disk but AFAIR this just walks you through the initial configuration and puts an icon on your desktop.  You can use this if you have a system which will boot windows but you really don't need it.

Most of the "compatibility" issues are a throwback to older systems using  modems which required OS level drivers.

---

### Post by peter1608 on 2009-03-10
Thanks for these responses, although I'm still rather confused by it all.  I was hoping there would be a plug and play interface so I wouldn't have to worry about the technicalities.

I think I'll go with my first choice (fibre optic cable isn't available in my postcode) and come back here for help if I need to.

Peter

---

### Post by Elfy on 2009-03-10
Basically - most if the 'big' ones will not support linux, what they mean is if youuuu get a problem they haven't got the cheat sheet for the 'support' people.

I use talktalk at the moment - used to be aol - all I really expect from them is that they support me up to the router, then if I do have any other issues I can come here. That said there is a talktalk forum which seems to have people using ubuntu and other distros.

I would echo blakemore though - I found that as long as I connect with lan then it just works - up until now I have no need to try and connect wirelessly.

Generally you can connect to the router and enter the necessary there without trouble.

---

