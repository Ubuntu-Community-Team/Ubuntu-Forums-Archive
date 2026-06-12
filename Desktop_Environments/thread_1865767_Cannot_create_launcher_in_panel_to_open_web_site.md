---
title: "Cannot create launcher in panel to open web site"
date: 2011-10-20
forum: Desktop Environments
---

### Post by wah fun on 2011-10-20
Hello,

Have just installed xubuntu 11.10 and this is my first foray into the Xfce desktop environment. I am moving away from the gnome desktop and do not want to go kde. Everything so far works just fine with one exception. I cannot create a custom launcher in the panel to access the following website (which is the Amazon seller account login page):

[https://www.amazon.com/ap/signin?_encoding=UTF8&openid.assoc_handle=usflex&openid.return_to=https%3A%2F%2Fwww.amazon.com%2Fgp%2Fseller-account%2Fmanagement%2Fyour-account.html%3Fie%3DUTF8%26ref_%3Dya_2&openid.mode=checkid_setup&openid.ns=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0&openid.claimed_id=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0%2Fidentifier_select&openid.pape.max_auth_age=900&openid.ns.pape=http%3A%2F%2Fspecs.openid.net%2Fextensions%2Fpape%2F1.0&openid.identity=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0%2Fidentifier_select](https://www.amazon.com/ap/signin?_encoding=UTF8&openid.assoc_handle=usflex&openid.return_to=https%3A%2F%2Fwww.amazon.com%2Fgp%2Fseller-account%2Fmanagement%2Fyour-account.html%3Fie%3DUTF8%26ref_%3Dya_2&openid.mode=checkid_setup&openid.ns=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0&openid.claimed_id=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0%2Fidentifier_select&openid.pape.max_auth_age=900&openid.ns.pape=http%3A%2F%2Fspecs.openid.net%2Fextensions%2Fpape%2F1.0&openid.identity=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0%2Fidentifier_select)

I know I can create a url launcher on the desktop but I prefer to keep my desktop uncluttered. I have done this just to test and it works perfectly.
I thought perhaps it had to do with the secure website but that isn't it because I have other launchers in the panel that access secure websites. 

I have googled for info on this problem but no usable info found. I have read Xfce documentation and I also reinstalled Xubuntu thinking it might just be a fluke but I still couldn't create this desired launcher. This is not an issue on my ubuntu gnome system.

If you can help with this issue, please reply.

---

### Post by gsmanners on 2011-10-20
You can't just drag a link into a panel, no. But you can create a launcher and then edit it to go wherever you want.

- Put a launcher into the panel (drag and drop or whatever)
- Right-click on it and select Properties
- Click on the edit button

In the "Command" field, put something like this:

```
exo-open --launch WebBrowser http://www.google.com/webhp?complete=0
```

The above example gives you Google without the annoying completion feature.

---

### Post by wah fun on 2011-10-27
Thanks for the suggestion. Your example works, but I cannot get this to work for my website (see above link). I can get to the Amazon home page but not to the seller account signin page. Again, as I said, creating a url link on the desktop works fine so I am a somewhat confused (not unusual). Other suggestions?

thx

---

### Post by wah fun on 2011-10-27
Thanks for the suggestion. Your example works, but I cannot get this to work for my website (see above link). I can get to the Amazon home page but not to the seller account signin page. Again, as I said, creating a url link on the desktop works fine so I am a somewhat confused (not unusual). Other suggestions?

thx

---

### Post by gsmanners on 2011-10-27
You could try using bookmarks in your browser. Not sure why you weren't doing that before, frankly. If that doesn't work then clearly your problem is with Amazon and not the OS/browser.

Another thing you could do is install a small wiki like didiwiki on your computer and then just point your browser at [http://localhost:8000/](http://localhost:8000/) to store URLs.

---

### Post by wah fun on 2011-10-28
Thank you again. Frankly, launching from the panel is just a personal preference for me and I have been able to do this with other sites that I use frequently. Creating the launcher for the Amazon login page has not been a problem before so I do not think it is site specific. I know how to and have already set the bookmark and created a url link on the desktop but since I cannot create the launcher in the panel, I am looking at this as more of a learning experience - on how to resolve a problem in linux. I am not new to linux but this one has me stumped. I am sure it is just something simple as most things really are.

Anyway, thanks again for your input.

Have a great day.

---

### Post by wah fun on 2011-10-28
OK. Thanks to wobblybob on the Debian board here is a workaround:

Re: Add a specific url launcher to Xfce panel

-------------
Postby wobblybob » 2011-10-18 13:27
Wow could Amazon make a longer url if it tried! Well I'm sure there is a better way to do this but I like making like easy so I pasted the url into the [http://www.tinyurl.com](http://www.tinyurl.com) site and got [http://tinyurl.com/36nlzau](http://tinyurl.com/36nlzau) then created a launcher using

Code: Select all
    firefox [http://tinyurl.com/36nlzau](http://tinyurl.com/36nlzau)


and when I click it it opens the correct url
---------------
This certainly makes the launcher work but it doesn't explain why this can't be done in the xfce panel itself. But a big THANK YOU to wobblybob and for other creative linux users who find ways to resolve issues. That's what makes the linux community great!

---

