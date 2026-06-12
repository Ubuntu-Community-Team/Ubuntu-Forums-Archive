---
title: "Webcam."
date: 2009-02-15
forum: General Help
---

### Post by Awesom on 2009-02-15
Well I have a webcam in my laptop and it worked with windows so I am just wondering what I have to do to have it working now with linux ?

---

### Post by Awesom on 2009-02-15
Anyone please?

---

### Post by cariboo on 2009-02-15
How about some details,  like what make of laptop it is, what is the output of lsusb. Open an Applications-->Accessories-->Terminal and type:

```
lsusb
```

Paste the output in your next post.

Also it is forum policy not to bump a post until 24 hours have elapsed. I didn't notice until I answered your post that you only posted your question half an hour ago.

Jim

---

### Post by Awesom on 2009-02-15
Oh sorry didn't know, now I do.. 

```

Bus 005 Device 004: ID 174f:a311  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000  


```

Thats what the lsus thing does and my laptop is an Asus thats almost all I know about it :P

---

### Post by Awesom on 2009-02-15
Please any suggestions ?

---

### Post by AlexBellisBrown on 2009-02-15
Go to add/remove programs, and search for a program called Cheese, install it and see if it detects your webcam automatically, if you havent tried already. :)

---

### Post by Awesom on 2009-02-15
:D Worked thanks man.

---

### Post by johnjohn2 on 2009-02-15
> **Awesom said:**
> :D Worked thanks man.

Cheese is good as is camorama

---

