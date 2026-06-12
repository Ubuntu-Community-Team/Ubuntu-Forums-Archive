---
title: "How can I enable the 3d desktop effect on my laptop"
date: 2007-05-19
forum: Desktop Effects &amp; Customization
---

### Post by yinglcs2 on 2007-05-19
Hi,

How can I enable the 3d desktop effect on my laptop? 
I see my laptop has a 'Graphics by ATI' label. But how can I know if it has the Prerequisites for this:

[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

Thank you.

---

### Post by Ub1476 on 2007-05-19
First check this: 
```
 glxinfo | grep direct
```

If, direct rendering: yes, then you can use 3d:)

If not, go to System>administration>enable restricted drivers manager. Enable your ati graphic driver. Restart. Type..

```
 glxinfo | grep direct
```

..again and if, direct rendering: yes, it's working. Now you need to install XGL and Beryl. Beryl is an eye-candy tool which gives you awesome 3d effetcs. Just search on Youtube.com:) 

Good guide to install XGL and Beryl here: [Linky]("http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_Beryl_.28ATI.29")

Scroll down to ..Alternate method: Using closed source FGLRX drivers from ATI.. and follow the guide from there.

Good luck:)

---

### Post by yinglcs2 on 2007-05-19
Thanks.  I reall I can just do 'Enable desktop effect' in the Preference menu in Ubuntu.

But now it is gone after I enable the driver??.  Can you please tell me where i can just enable desktop effect?

---

### Post by yinglcs2 on 2007-05-19
From the documentation:

    * Disable the universe repositories (these provide Beryl software that is incompatible with the fglrx driver). 

Go to System > Administration > Software Sources 
Uncheck Community-maintained Open Source software (universe)
Click Close

If that is the case, can you please tell me what version of Beryl that I will install?
Is that the latest verion availabe?

---

### Post by Ub1476 on 2007-05-20
As I said.. You most first check this:

```
 glxinfo | grep direct
```

..to see if 3d is already working (direct rendering:yes). If it is, I don't think you need to install graphic drivers. 

You will install version 0.2.0. Newest v. is 02.1. but there's a little bug with XGL and the update, so you need to wait a little. Doesn't do much anyway:) 

Now, new ATI cards works best with XGL (closed source), but you may try open source (AIGLX) if you got an old ATI card.

---

