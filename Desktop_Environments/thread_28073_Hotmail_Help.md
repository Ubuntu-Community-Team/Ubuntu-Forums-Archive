---
title: "Hotmail Help"
date: 2005-04-18
forum: Desktop Environments
---

### Post by CARGANZAR on 2005-04-18
Hi

Does Anyone Know How To Setup The Evolution Email To Recieve Msn Hotmail Any Help Would Be Greatly Appreciated. :???:

---

### Post by andvaranaut on 2005-04-18
[QUOTE=CARGANZAR]Hi

Does Anyone Know How To Setup The Evolution Email To Recieve Msn Hotmail Any Help Would Be Greatly Appreciated. :???:[/QUOTE]
 As far as I know this is not possible. You know, MSN likes to keep its things to itself ;)

However, there is a rather workable solution using a program called 'gotmail'. If I recall correctly it is in the 'universe' repository. Gotmail will allow you to download your Hotmail emails to a mbox file on your local hard drive. Besides being a great backup, that mbox file may be directly opened by Evolution (set up a 'local' mailbox and point it to the file), so that you may locally access your Hotmail emails.

If you add a cron job to automatically run gotmail every 10 minutes or so, you will essentially achieve what you want. Note that this setup won't allow you to send email with Hotmail via Evolution.

Hope this helps.

---

### Post by CARGANZAR on 2005-04-18
Yer Cheers This Should Help

I'll Give It A Go In The Morning. Ive Only Just Installed A Few Hours Ago And Already I Think This System Is Great.

Forget Windows Try A Hedgehog \\:d/

---

### Post by swalsh on 2005-04-29
How does this work with Thunderbird?  I found the gotmail file, but I'm not sure on how to use it.

---

### Post by Yolteotl on 2005-04-29
There is an extension for Thunderbird called [WebMail](http://webmail.mozdev.org/), that'll let you get mails from Hotmail.

---

### Post by swalsh on 2005-04-30
Thanks, downloading right now.

---

### Post by treris on 2005-05-12
So i've downloaded and installed this webmail extension for thunderbird, i've set it up to use port 1110 because 110 is blocked by Kubuntu(??) and it's working on like small mails but it freezes up on mails that have attachments. 

Can anybody help me ??? 

PS I've also done the things listed on the extension's website but it's still freezing GRRRRRR

-----------------

Never mind I've gotten Hotwayd to work for me just fine, thank god, although my hotmail accounts are not my main accounts, but still I have a lot of people using them

---

### Post by Psquared on 2005-06-08
I can't even download the extension. Normally Thunderbird does this itself, but the Web Mail extension is not listed. It won't even download to a file in Firefox.

---

### Post by Psquared on 2005-06-08
[QUOTE=Yolteotl]There is an extension for Thunderbird called [WebMail](http://webmail.mozdev.org/), that'll let you get mails from Hotmail.[/QUOTE]

According to the Mozilla site this doesn't work.

---

### Post by mike998 on 2005-06-08
[QUOTE=CARGANZAR]Yer Cheers This Should Help

I'll Give It A Go In The Morning. Ive Only Just Installed A Few Hours Ago And Already I Think This System Is Great.

Forget Windows Try A Hedgehog \\:d/[/QUOTE]

You Appear To Suffer From Premature Capitalization...

---

### Post by ubuntu_fire on 2005-06-08
there are several third party applications that will get hotmail email and all you have to do in you email client is set the server to localhost.  
I use Freepops because it does yahoo and many others.  However, there are others:
gotmail
mr postman

Choose the one you like.  
If all else fails look at the setup files from the different application you choose.

---

### Post by Psquared on 2005-06-08
[QUOTE=ubuntu_fire]there are several third party applications that will get hotmail email and all you have to do in you email client is set the server to localhost.  
I use Freepops because it does yahoo and many others.  However, there are others:
gotmail
mr postman

Choose the one you like.  
If all else fails look at the setup files from the different application you choose.[/QUOTE]


I don't know about freepops, but "hotwayd" and "gotmail" no longer work with Hotmail. Fetchyahoo works great for yahoo mail, but thats because yahoo is not as threatened by Linux as M$ is.

If Redmond spent as much time improving their products as they do making them secret and proprietary the world would be a better place to live.

---

### Post by frodon on 2005-09-05
[QUOTE=andvaranaut]As far as I know this is not possible. You know, MSN likes to keep its things to itself ;)

However, there is a rather workable solution using a program called 'gotmail'. If I recall correctly it is in the 'universe' repository. Gotmail will allow you to download your Hotmail emails to a mbox file on your local hard drive. Besides being a great backup, that mbox file may be directly opened by Evolution (set up a 'local' mailbox and point it to the file), so that you may locally access your Hotmail emails.

If you add a cron job to automatically run gotmail every 10 minutes or so, you will essentially achieve what you want. Note that this setup won't allow you to send email with Hotmail via Evolution.

Hope this helps.[/QUOTE]THx for the tips, i didn't know this way and i enjoy using it now.

---

### Post by madjo on 2005-09-05
I recently installed Hotwayd and it seems to work for me... within minutes I was able to download my hotmail mail into my mailclient (Opera's M2)

---

### Post by frodon on 2005-09-05
[QUOTE=madjo]I recently installed Hotwayd and it seems to work for me... within minutes I was able to download my hotmail mail into my mailclient (Opera's M2)[/QUOTE]Does hotwayd make a copy of your mails on your computer or does it move (clear the mails on your hotmail page) all the mails on your computer ?

---

