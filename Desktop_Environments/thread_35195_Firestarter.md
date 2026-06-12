---
title: "Firestarter"
date: 2005-05-18
forum: Desktop Environments
---

### Post by spencer on 2005-05-18
I have Port 80 and port 113 open when I do a check wth either sygate or shields up test. Would installing firestarter block these ports? I have read other post here about their computers being completly stealthed. Does anybody else have these ports open?

-spencer

---

### Post by concept10 on 2005-05-18
Yes, you could block whatever port(s) you want to block, you might block some services 
that you currently use.  Port 113 is used by a variety of services like IRC, instant messaging, etc.

Firestarter has some great common sense documentation:

[http://www.fs-security.com/docs/policy-page.php](http://www.fs-security.com/docs/policy-page.php)

---

### Post by spencer on 2005-05-18
Sounds good, i'll install it and read the documentation. 

Thanks.

---

### Post by spencer on 2005-05-18
With Firestarter I'm having the same problem, port 80 and 113 are still closed but not stealthed. I guess this is normal for windows and linux. My mac is entirely stealthed and I've always had this trouble with windows and linux, yet I've heard of others using windows and linux that are stealthed. Do I need another program? Surely it's possible, I wonder how they do it. I've added a rule in Firestarter to block port 80 and 113. Where have I gone wrong? Maybe it's with me? :?

Any explanations would be welcome. Thanks.

-spencer

---

### Post by spencer on 2005-05-18
Would anyone at least be willing to tell me if the are fully stealthed on port 80 and 113 on these test sites or tell me to bug off? I'll read firstarter manual again but I don't remember seeing anything on how to block ports. Maybe these ports need to be opened? I know that blocking outbound doesn't let me browse the net, but that's not what I want. 

-spencer

---

### Post by sunset_studies on 2005-05-19
Is the Mac on the same network? If not, it could be your router that has these ports open.

What programs are listening on the ports you speak of? 

sudo netstat -tlp

should tell you.

---

### Post by spencer on 2005-05-19
No, mac is not on the same network. That must be it. And yes, it must be my router. Now to figure how the router out. When does it end?  :roll: 

I did "sudo netstat -tlp" and it lists 3 different PID/Program names that are lisening. Is this info something I shouldn't send over the net? since you said "Should you tell".

---

### Post by sunset_studies on 2005-05-19
is this the output from the command?


```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN     9012/cupsd
tcp        0      0 localhost.localdom:smtp *:*                     LISTEN     8110/master
tcp6       0      0 ip6-localhost:smtp      *:*                     LISTEN     8110/master

```


I think this is  what one would expect from a default Ubuntu install.

You can see the actual port numbers by executing *netstat -tnlp*

In the above output, cupsd is listening on 631 and master on 25.

If 80 and 113 don't show up, I'd say it is your router.

---

### Post by spencer on 2005-05-20
My numbers are slightly different from yours, My cupsd is listening on a different number from yours and the two masters are also different numbers. How do I execute netstat -tnlp? Is it with sudo netstat -tnlp? 

I think it is this router. I'm gonna have to figure out how to do this. Is configuring a router for the technical minded? Sounds like I'll have to do a lot of work. I have mine set at whatever defaults it comes with. I figure it's pretty safe with the defaults, is this true? On the second thought maybe it's not since port 80 and 113 don't pass the test.

-spencer

---

### Post by sunset_studies on 2005-05-20
> My numbers are slightly different from yours, My cupsd is listening on a different number from yours and the two masters are also different numbers. 

Sorry, the example output was from a *sudo netstat -tlp* execution, not a *sudo netstat -tnlp* execution. The numbers in the example output are the ids of each process and the difference you  mention is to be expected. If I were to restart one of those services (cupsd for example), the PID of the service would change and this change would show up if I were to run netstat again.
To repeat: the example output does not show any port numbers at all.


> How do I execute netstat -tnlp? Is it with sudo netstat -tnlp?  

yes.


> I think it is this router. I'm gonna have to figure out how to do this. Is configuring a router for the technical minded? Sounds like I'll have to do a lot of work. I have mine set at whatever defaults it comes with. I figure it's pretty safe with the defaults, is this true? On the second thought maybe it's not since port 80 and 113 don't pass the test. 

It all depends on the brand and model of the router. Try a Google search for any known exploits for your model.

---

### Post by spencer on 2005-05-20
Thanks for the info, it is very clear and concise and That's always nice. :)
The router I'm using is an older D-Link DI-604. I'm doing some research on it right now and it includes some Google searches. Thanks.

-spencer

---

### Post by spencer on 2005-05-24
Well, I'm now stealthed, at least according to all the test sites I've tested with. I did it using this easy to understand guide [http://support.dlink.com/faq/view.asp?prod_id=1068](http://support.dlink.com/faq/view.asp?prod_id=1068). Firestarter is for the extra peace of mind. I hope this helps anyone else that with a D-Link DI-604. Lovin' Ubuntu and all it does. :-P Looking forward to using future releases. Thanks Ubuntu... 

-spencer

---

