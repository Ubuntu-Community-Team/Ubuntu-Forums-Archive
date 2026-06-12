---
title: "Ubuntu won't start"
date: 2009-06-17
forum: General Help
---

### Post by andreazana on 2009-06-17
Hello, I was wondering if somebody has the solution of my problem...

It's not that my Hardy Heron won't start at all, but it only starts eventually. I select Ubuntu from the list of OS (I have Ubuntu and Windows on this pc), the splash window appears and it stays like that until the end of the days. Quite annoying. I procceed to restart and try again and again, until Ubuntu finally loads the authentication. Is there any solution for this? Is there a possibility that Ubuntu won't start at all one of this days?

I'm desperate! Any help would be very appreciated.

Thanks.

---

### Post by andreazana on 2009-06-17
Hello, I was wondering if somebody has the solution of my problem...

It's not that my Hardy Heron won't start at all, but it only starts eventually. I select Ubuntu from the list of OS (I have Ubuntu and Windows on this pc), the splash window appears and it stays like that until the end of the days. Quite annoying. I procceed to restart and try again and again, until Ubuntu finally loads the authentication. Is there any solution for this? Is there a possibility that Ubuntu won't start at all one of this days?

I'm desperate! Any help would be very appreciated.

Thanks.

---

### Post by cariboo on 2009-06-17
Could you open an Application-->Accessories-->Terminal and type:

```
dmesg > dmesg.txt
```

the above command will pipe the output of the above command to a test file called dmesg.txt. Once the file is created right-click on it and select Create Archive..., just click the create button and it will create an archive called dmesg.txt.tar.gz. Attach this file to your next post by using the advanced editor and clicking the Manage Attachment button.

---

