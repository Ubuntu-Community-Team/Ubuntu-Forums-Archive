---
title: "USB modem drops connection"
date: 2005-10-24
forum: Desktop Environments
---

### Post by jimbob on 2005-10-24
I can dial up numbers just fine but for some strange reason instead of receiving the login prompt, the modem drops the line.   Here is the dialog from /var/log/syslog:

  Oct 24 16:24:02 localhost pppd[8323]: pppd 2.4.3 started by root, uid 0
Oct 24 16:24:03 localhost chat[8324]: abort on (BUSY)
Oct 24 16:24:03 localhost chat[8324]: abort on (NO CARRIER)
Oct 24 16:24:03 localhost chat[8324]: abort on (VOICE)
Oct 24 16:24:03 localhost chat[8324]: abort on (NO DIALTONE)
Oct 24 16:24:03 localhost chat[8324]: abort on (NO DIAL TONE)
Oct 24 16:24:03 localhost chat[8324]: abort on (NO ANSWER)
Oct 24 16:24:03 localhost chat[8324]: abort on (DELAYED)
Oct 24 16:24:03 localhost chat[8324]: send (ATZ^M)
Oct 24 16:24:03 localhost chat[8324]: expect (OK)
Oct 24 16:24:03 localhost chat[8324]: ATZ^M^M
Oct 24 16:24:03 localhost chat[8324]: OK
Oct 24 16:24:03 localhost chat[8324]:  -- got it
Oct 24 16:24:03 localhost chat[8324]: send (ATDT9720255^M)
Oct 24 16:24:03 localhost chat[8324]: expect (CONNECT)
Oct 24 16:24:03 localhost chat[8324]: ^M
Oct 24 16:24:36 localhost chat[8324]: ATDT9720255^M^M
Oct 24 16:24:36 localhost chat[8324]: CONNECT
Oct 24 16:24:36 localhost chat[8324]:  -- got it
Oct 24 16:24:36 localhost chat[8324]: send (^M)
Oct 24 16:24:36 localhost chat[8324]: expect (ogin:)
Oct 24 16:24:36 localhost chat[8324]:  53333 V42bis^M
Oct 24 16:24:56 localhost chat[8324]: ^M
Oct 24 16:24:56 localhost chat[8324]: NO CARRIER
Oct 24 16:24:56 localhost chat[8324]:  -- failed
Oct 24 16:24:56 localhost chat[8324]: Failed (NO CARRIER)
Oct 24 16:24:56 localhost pppd[8323]: Connect script failed
Oct 24 16:24:57 localhost pppd[8323]: Exit.

  Anyone seen this before?

  Wouldn't you just know it, Windows works just fine so it can't be a hardware thing.

   Any ideas gratefully accepted.  :???:

---

### Post by migueljacq on 2005-10-24
Looks to me like the configuration. Something in the script either clashes or is missing something. What sort of protocol is it? PAP, CHAT, CHAP? 
How did you configure the modem? pppconfig? I would check basic things first like phone number, username and password, etc first, as a process of elimination. Certainly not a hardware problem.

EDIT: On a closer look, looks like CHAT. I don't know chat myself, I use pap. But I would recommend looking at things in the configuration like whether it's been set to demand authentication from the ISP's server etc.

---

### Post by jimbob on 2005-10-24
I was using CHAT but I tried pap and chap with the same result.

The question is, what is Windows doing differently that allows the line to stay up?

Thanks for answering ...

---

### Post by Dria on 2005-11-04
A couple of hints for you to think about:

- I think with CHAP authentication you should use "user" instead of "login" on the login script.

- My "winmodem" behave the same as yours if I don't add a "ATX3" on the init strings.

VERY useful for me was the page found at [http://www.theory.physics.ubc.ca/ppp-linux.html]("http://www.theory.physics.ubc.ca/ppp-linux.html")

---

### Post by jimbob on 2005-11-09
Happy ending at last!  I had tried everything with Gppp to no avail and last nite
I installed Kppp on standard Ubuntu and guess what - it works!  Keep in mind that I had used Gppp successfully on many lines throughout the Eastern US, but this Verizon line here in NY would absolutely not function.  

I think it has something to do with the initialization string sent to the modem but I really don't know which parameter is the culprit.

Modem init strings seem to be some sort of black art.  :p :p :p

---

### Post by drummer44 on 2005-12-22
Hi,
I am having the same problems on my setup.  I got the NO CARRIER response when my external US Robotics 56K modem dialed-out.  I am currently either using "Pon" or "Administrator-Network".  I am not sure what set of files are used between these two.  However, running "sudo plog" allowed me to see that I was getting a NO CARRIER response.  I have been wondering about the modem init string and how that affects this whole process.  I will look into what you have shared.  
Thanks for sharing!!

---

