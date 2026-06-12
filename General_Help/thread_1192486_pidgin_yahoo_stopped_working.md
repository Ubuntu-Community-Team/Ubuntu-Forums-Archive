---
title: "pidgin yahoo stopped working"
date: 2009-06-20
forum: General Help
---

### Post by Elijah on 2009-06-20
Hi, 

Pidgin with yahoo messenger used to work, I have two accounts on it and 1 msn account. 

The msn account still logs in , but both yahoo accounts stopped logging in... I tried upgrading pidgin but the issue is still here :( 

Anyone noticed this? How do I fix this? 



Best regards, 
Elijah

---

### Post by DanFlo on 2009-06-20
Check this thread!
It worked like a charm for me :
[http://ubuntuforums.org/showpost.php?p=7487480&postcount=3](http://ubuntuforums.org/showpost.php?p=7487480&postcount=3)

---

### Post by Elijah on 2009-06-20
Thanks! this worked. 

But why did it suddenly happen? maybe something to do with the yahoo servers ? Is this change permanent or will the pidgin devs be able to adapt to this?

---

### Post by Tech Provider on 2009-06-21
It stopped working cause yahoo changed something regarding their server access. 
This is another simple fix : [Pidgin stopped working - Fix]("http://ubuntuswitch.blogspot.com/2009/06/pidgin-stopped-working-fix.html")

---

### Post by harlequinade on 2009-06-21
> **DanFlo said:**
> Check this thread!
It worked like a charm for me :
[http://ubuntuforums.org/showpost.php?p=7487480&postcount=3](http://ubuntuforums.org/showpost.php?p=7487480&postcount=3)

Yeesssss!!...Worked first time! Thanks, guys - you're priceless :D

---

### Post by Elijah on 2009-06-23
meh, it stopped working again! 'Connection Refused'! 

Are there other alternatives to pidgin?

---

### Post by Sentience on 2009-06-23
> **DanFlo said:**
> Check this thread!
It worked like a charm for me :
[http://ubuntuforums.org/showpost.php?p=7487480&postcount=3](http://ubuntuforums.org/showpost.php?p=7487480&postcount=3)

This did not work for me. Was there any special way I was supposed to add the 66.163.181.184 scs.msg.yahoo.com to the file?

---

### Post by Sentience on 2009-06-23
> **Tech Provider said:**
> It stopped working cause yahoo changed something regarding their server access. 
This is another simple fix : [Pidgin stopped working - Fix]("http://ubuntuswitch.blogspot.com/2009/06/pidgin-stopped-working-fix.html")

This worked yesterday but not today. Still not working.

---

### Post by Wiebelhaus on 2009-06-23
Go to Accounts->Select your YM screen name->Edit Account->Advance.

Then change the original value of &#8220;scs.msg.yahoo.com&#8221; to any of these ip address:
66.163.181.183, 66.163.181.166 , 66.163.181.169, 66.163.181.170, 66.163.181.172, 66.163.181.171, 66.163.181.181, [COLOR="Red"]66.163.181.182[/COLOR]


One in red works for me!

---

### Post by Sentience on 2009-06-23
> **Wiebelhaus said:**
> Go to Accounts->Select your YM screen name->Edit Account->Advance.

Then change the original value of “scs.msg.yahoo.com” to any of these ip address:
66.163.181.183, 66.163.181.166 , 66.163.181.169, 66.163.181.170, 66.163.181.172, 66.163.181.171, 66.163.181.181, [COLOR="Red"]66.163.181.182[/COLOR]


One in red works for me!



Not working. It worked for me yesterday but today this fix isnt working.

---

### Post by redmk2 on 2009-06-23
The addresses listed [**_here_**]("http://ubuntuforums.org/showthread.php?t=1191064") still work.

---

### Post by Elijah on 2009-06-24
I tried the newer version, still no go... 

I'm going back to meebo.com for now :(

---

