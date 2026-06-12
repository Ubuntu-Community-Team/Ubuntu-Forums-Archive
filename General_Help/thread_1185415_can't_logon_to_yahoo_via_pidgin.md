---
title: "can't logon to yahoo via pidgin"
date: 2009-06-12
forum: General Help
---

### Post by silentIm on 2009-06-12
hi all,

I just installed ubuntu jaunty on compaq presario b1200. I tried pidgin as messenger for yahoo account, but it fails to connect (server timeout). But my msn account works only if i check http method option in advanced tab.

Any idea to fix this? Thank you for your reply.

---

### Post by colau on 2009-06-12
> **silentIm said:**
> hi all,

I just installed ubuntu jaunty on compaq presario b1200. I tried pidgin as messenger for yahoo account, but it fails to connect (server timeout). But my msn account works only if i check http method option in advanced tab.

Any idea to fix this? Thank you for your reply.
How did you try to connect to yahoo?
Selecting the yahoo you just have to put your id without "@yahoo.com" and give the password.

---

### Post by silentIm on 2009-06-12
I've done that already, but still doesn't work.

---

### Post by colau on 2009-06-12
> **silentIm said:**
> I've done that already, but still doesn't work.
From pidgin>Accounts>Manage Accounts
Is the yahoo account checked?

---

### Post by silentIm on 2009-06-12
yes, i've checked it from the beginning. Still not work.

---

### Post by colau on 2009-06-12
> **silentIm said:**
> yes, i've checked it from the beginning. Still not work.
Uncheck all id except yahoo id.
See is there any contact in pidgin with that yahoo id?

---

### Post by silentIm on 2009-06-12
I even check all options in buddies->show. but the status bar still show connecting message. I ping scs.msg.yahoo.com, it shows reply, but the connection is not established.

---

### Post by colau on 2009-06-12
> **silentIm said:**
> I even check all options in buddies->show. but the status bar still show connecting message. I ping scs.msg.yahoo.com, it shows reply, but the connection is not established.
Can you post
```

pidgin --version

```

---

### Post by mharrison on 2009-06-12
Open your Yahoo account settings.  Under the server options, replace the scs.msg.yahoo.com with scs-dcnb.msg.yahoo.com and see if that lets you connect.

---

### Post by silentIm on 2009-06-12
are you sure scs-dcnb.msg.yahoo.com is correct? i can;t ping it.
pidgin version is 2.5.5

---

### Post by colau on 2009-06-12
> **silentIm said:**
> are you sure scs-dcnb.msg.yahoo.com is correct? i can;t ping it.
pidgin version is 2.5.5
Can you post snapshots from 
```

pidgin>Accounts>Manage Accounts>Selecting a yahoo id>Modify>Advanced
pidgin>Accounts>Manage Accounts>Selecting a yahoo id>Modify>Basic

```

---

### Post by mharrison on 2009-06-12
Sorry, try 66.163.181.189 instead.  Verified this on my system.

---

### Post by silentIm on 2009-06-12
Still not working. The connecting time is forever.
I don't know if it is related or not, but i found i can't establish video chat as well when using yahoo client on windows since I came to Melbourne. When I'm in Indonesia there is no problem.

At first I thought it is something to do with firewall in my unit owner i live with. But I tried to connect through my uni access point and still the same. 

screeshots in the attachment.

---

### Post by SwedishWings on 2009-06-21
Have you seen this?

[http://jimmod.com/blog/2009/06/solving-pidgin-cannot-connect-ym/](http://jimmod.com/blog/2009/06/solving-pidgin-cannot-connect-ym/)

/Mike

---

### Post by rplomantes on 2009-06-21
it should be cs101.msg.mud.yahoo.com
see this link [http://necoda.com/uncategorized/yahoo-messenger-not-working-on-pidgin](http://necoda.com/uncategorized/yahoo-messenger-not-working-on-pidgin)

---

### Post by trungd_t on 2009-06-21
Similar solution: [http://webupd8.blogspot.com/2009/06/pidgin-256-yahoo-fix.html](http://webupd8.blogspot.com/2009/06/pidgin-256-yahoo-fix.html)

---

### Post by wncben on 2009-06-23
Instead of putting a 'server change bandaid' on pidgin, why not update it to the newer version which fixes the problem?  Yahoo is phasing out the older protocols and switching servers will only fix the problem until yahoo updates the server. Check here for instructions on how to update pidgin and it will automatically update too!  
[http://ubuntuforums.org/showpost.php?p=7504859&postcount=10](http://ubuntuforums.org/showpost.php?p=7504859&postcount=10)
~Cheers

---

### Post by statprog on 2009-11-06
hi guys i just changed the [COLOR="Magenta"]proxy type[/COLOR] under [COLOR="Blue"]proxy option [/COLOR]to (no proxy)and unchecked yahoo japan and pidgin work properly and connect to yahoo account

---

