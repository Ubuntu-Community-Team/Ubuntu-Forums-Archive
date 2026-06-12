---
title: "Could not update ICEauthority file /home/carl/.ICEauthority"
date: 2010-09-18
forum: Desktop Environments
---

### Post by c-m on 2010-09-18
Hi,

Every time i start up i am getting the following error

```
Could not update ICEauthority file /home/carl/.ICEauthority
```

I checked the file and I was the owner and it was set to read/write yet i was unable to delete it.

I deleted the file as root and attempted to log in again. 

Once logged in i got the exact same message:

Could not update ICEauthority file /home/carl/.ICEauthority

---

### Post by Old *ix Geek on 2010-09-19
> **c-m said:**
> Every time i start up i am getting the following error

```
Could not update ICEauthority file /home/carl/.ICEauthority
```

I checked the file and I was the owner and it was set to read/write yet i was unable to delete it.

I deleted the file as root and attempted to log in again. 

Once logged in i got the exact same message:

Could not update ICEauthority file /home/carl/.ICEauthority

Does that file exist now? If so, do this:

```
chmod 777 ~/.ICEauthority
```

and try again. If that doesn't solve it, try this:

```
chmod 777 ~/.ICEauthority; chmod 1777 /tmp
```

If it's still not working, or if the file no longer exists, post again.

---

### Post by c-m on 2010-09-19
Tried both with no success.

It seems that my home directory had changed ownership from my user carl to 1096 whoever that is.

I opened it as root and changed it back and it worked fine.

Thanks

---

### Post by ttguy on 2010-09-22
```
Could not update ICEauthority file /home/carolyn/.ICEauthority  
(usr/lib/libgconf2-4/gconf-sanity-check-2 has quit with state 256 
Nautilus cannot create the following folders : /home/carolyn/Desktop and /home/carolyn/.nautilus
```Another thing to check if you get this sort of error is the ownership and permissions of the /home folder.

My system generated this error when I recently moved the drive that home lived on. Strangely I could log on under my userid but other users could not log in.

It turned out that when I created the /home folder (into which I mounted my new drive) I created it so that I owned it. 
Thus, only I could create .ICEauthority files in /home/<userid>. 
After setting ownership and group of /home to root and the permissions to
 rwxr-xr-x all my users could log in.

---

### Post by chocobanana on 2010-09-22
That happened to me a few times before. 

Chmod is  a solution but deleting the offending file is simpler.

From a terminal (e.g. press Ctrl+Alt+F2 and log in):
```
rm ~/.ICEauthority
```

Good luck

---

