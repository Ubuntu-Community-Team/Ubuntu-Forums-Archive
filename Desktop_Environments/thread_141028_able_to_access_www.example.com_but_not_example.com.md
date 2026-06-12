---
title: "able to access www.example.com but not example.com"
date: 2006-03-07
forum: Desktop Environments
---

### Post by UTI351 on 2006-03-07
hello. this is a strange  thing.  i installed ubuntu from the original free cd, everything works properly except one thing. i don't know what's  happening. if i try to access [http://www.mywebsiteexampledomain.com](http://www.mywebsiteexampledomain.com) the site opens but when i try t access [http://mywebsiteexampledomain.com](http://mywebsiteexampledomain.com) I receive the following error "The connection was refused when attempting to connect to mywebsiteexampledomain.com". I'm using Ubuntu 5.10 and this  happens only under Ubuntu.  and i tried   accessing the site from another Ubuntu computer and  have the same problem. If i try to access with ww. or without www. in the  domain name from Windows system  the pages  appear. Please, i'm a noobie, help me. ;(

---

### Post by aggiechemist on 2006-03-07
Are you using firefox in both cases? Or did you switch to IE on the Windows box?

Sometimes pages just don't exist without the "www". Some browsers automatically try to add www if the site doesn't work, other broswers don't do that. Maybe try another browser and see what happens (I go back and forth from Firefox, Opera, Mozilla, and Konqueror).

Also, is there a specific webpage? Or does it not matter where you are going?

---

### Post by cyberb0b on 2006-03-07
This is a web browser feature.  I'm assuming you are using firefox.

In firefox, enter "about:config" in the location bar and type "fixup" in the filter field.  You should see these three entries:

```

browser.fixup.alternate.suffix   default  string   .com
browser.fixup.alternate.enabled  default  boolean  true
browser.fixup.alternate.prefix   default  string   www.
```

Thus, entering "ubuntu" as the address takes me to "www.ubuntu.com" after the address is fixed up.  The setting that is probably wrong in your case is the "enabled" flag.

---

### Post by UTI351 on 2006-03-07
Under Ubuntu 5.10 *
- I used firefox and opera . the error that i receiv it happens in random and there is no specific website/domain that  shows  this kind of problem.
- like i said in Ubuntu most of the time (in random websites) I'm not able to access the domain/s without www.

Under  Windows *
- When Using Firefox, IE or Opera I'm able to access  all sites with or without www.

And yet, this beats me, don't have a clue  why this happens.

---

### Post by UTI351 on 2006-03-07
[QUOTE=cyberb0b]This is a web browser feature.  I'm assuming you are using firefox.

In firefox, enter "about:config" in the location bar and type "fixup" in the filter field.  You should see these three entries:

```

browser.fixup.alternate.suffix   default  string   .com
browser.fixup.alternate.enabled  default  boolean  true
browser.fixup.alternate.prefix   default  string   www.
```

Thus, entering "ubuntu" as the address takes me to "www.ubuntu.com" after the address is fixed up.  The setting that is probably wrong in your case is the "enabled" flag.[/QUOTE]

thank you. i will try that and will get back to the forum, with my update.

i appreciate your  support.

---

### Post by cyberb0b on 2006-03-07
One more thing.  If you are unable to reach a website, or the website doesn't exist, such as [http://notawebsiteatallishere.com/](http://notawebsiteatallishere.com/) the error message will not have the www. prefix in there.

So make sure you try entering the prefix manually and see if that fails to connect once in a while.  That is, the same error page shows up when you try to visit [http://www.ubuntu.com](http://www.ubuntu.com) as when you enter [http://www.notawebsiteatallishere.com/](http://www.notawebsiteatallishere.com/)

If the error page shows up with www. in there, this is a connection problem.  My guess would be invalid DNS nameservers in your network configuration causing firefox to timeout.

---

