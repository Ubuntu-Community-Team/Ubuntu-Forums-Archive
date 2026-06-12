---
title: "copying contents through ssh"
date: 2011-06-30
forum: Desktop Environments
---

### Post by de1337ed on 2011-06-30
I want to copy the contents of a directory through ssh. The problem I'm having is that I can use the cp -r terminal function, but that would cause the directory itself to also be copied. I just simply want whats inside to be copied to another directory. Because of the way I have my server laid out, I would have to copy the entire directory, then copy each element one by one inside that directory into the specified folder. This is really tedious. So, is there a way I can just copy its contents? I was thinking of zipping it, the unzipping it, but when you extract, it once again just creates a new directory, not the contents inside. Help please!

If this is confusing, this is what I'm trying to do:
Directory: ../random/
Currently after scp -r:
/home/blah/blah/random/(elements inside random)
what I want:
/home/blah/blah/(elements inside random)

---

### Post by i.r.id10t on 2011-06-30
scp -r username@hostname:/path/to/random/* .

---

### Post by nmaster on 2011-06-30
do you want to try using wildcards like '*'? its not clear what you are doing or what you want to do.  could you just post the command you are trying to execute? then we can work together to modify that.

---

### Post by de1337ed on 2011-06-30
> **nmaster said:**
> do you want to try using wildcards like '*'? its not clear what you are doing or what you want to do.  could you just post the command you are trying to execute? then we can work together to modify that.

Sorry if I'm unclear. But basically, i'm running the following command:

scp -r /path/to/directory/ username@server:/path/to/location

the issue is, that when i do this, i get the following at the server end:
/path/to/location/directory/. So like i get the entire directory copied. I just want the contents inside directory to be copied without them being wrapped in the directory. 
So instead of /location/directory/"contents" i want /location/"contents". the issue is that scp -r takes the entire directory. The only other way i can think is if I copy each file inside the directory individually which can be very tedious.

---

### Post by de1337ed on 2011-07-01
*bump* sorry, really need an answer.

---

### Post by e79 on 2011-07-01
```
cd /location/directory
```

```
scp * username@server:/path/to/location
```

Cheers

---

### Post by e79 on 2011-07-01
> **de1337ed said:**
> *bump* sorry, really need an answer.

So, did that helped ?

---

### Post by nmaster on 2011-07-01
> **e79 said:**
> ```
cd /location/directory
``````
scp * username@server:/path/to/location
```Cheers

sorry for not responding earlier.  e79 is right.  without the 'cd':
```
scp /location/directory/* username@server:/path/to/location
```

for more info on using wildcards at the command line: [http://www.robelle.com/smugbook/wildcard.html](http://www.robelle.com/smugbook/wildcard.html)

---

### Post by e79 on 2011-07-01
I'm glad you could solve your issue !

Cheers

e79

---

### Post by de1337ed on 2011-07-06
> **e79 said:**
> I'm glad you could solve your issue !

Cheers

e79

Sorry for responding so late, I went on vacation, so no laptop. Tried it right now and it worked. Thanks a lot everyone :popcorn:

---

