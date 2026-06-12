---
title: "gdesklet starter bar + firefox = university of minnesota? Whaaat?"
date: 2005-04-26
forum: Desktop Environments
---

### Post by Rehevkor on 2005-04-26
This defies reason.

I installed gdesklets and downloaded the starter bar desklet for it. I started the desklet and added launchers to it by dragging them from the Applications menu. All seemed well until I launched the Firefox shortcut that I had dragged to the starter bar. Instead of loading my usual start page - these forums - it took me [here](http://www1.umn.edu/twincities/index.php). What the hell?

I checked the default start page in the Firefox preferences, and it was still set to [www.ubuntuforums.org](www.ubuntuforums.org). I've looked through all of the options on gdesklets and that desklet in particular (even its source) and I can't find any explanation for this.

---

### Post by shakin on 2005-04-26
That's rather odd. I don't have that problem.

Edit the FF starter bar icon and see if there is a url paramater on the command. The only difference I made was not dragging shortcuts from the menu. I just typed in the command name for each one, so maybe starter bar has a little trick where it directs you to that domain.

---

### Post by wolovids on 2005-04-26
View the properties of that launcher.  Change the executable from ```
firefox %u
``` to just ```
firefox
```

Hopefully that works.

---

### Post by shakin on 2005-04-26
I just ran strings on the starterbar source and couldn't find that url.

---

### Post by spencer on 2005-04-26
Hello,

I have the same issue. Take a look at my post [URL=http://ubuntuforums.org/showthread.php?s=6dfbada7f29f817397c68d52aacaf0
d2&t=29944]here[/URL]. This is no good [-X .

-spencer

---

### Post by Rehevkor on 2005-04-26
[QUOTE=wolovids]View the properties of that launcher.  Change the executable from ```
firefox %u
``` to just ```
firefox
```

Hopefully that works.[/QUOTE]

I tried that, nothing changed.

---

### Post by ssam on 2005-04-26
i think that is the result of a google i'm feeling luck for "%u" (put %u in the location bar of firefox and hit enter).

when gnome uses launches firefox then %u is replaced with a web site address if you asked for one. ie if you click a link to a home page in an about box in some program, then that addess replaces the %u
gdesklets must not have this feature, so it pass %u as an address.

---

### Post by chz on 2005-05-04
[QUOTE=ssam]i think that is the result of a google i'm feeling luck for "%u" (put %u in the location bar of firefox and hit enter).

when gnome uses launches firefox then %u is replaced with a web site address if you asked for one. ie if you click a link to a home page in an about box in some program, then that addess replaces the %u
gdesklets must not have this feature, so it pass %u as an address.[/QUOTE]
 thats kind of like when you type http;// with a semicolon instaed of a colon in the address bar...it takes you to microsoft.com....

---

### Post by tread on 2005-05-04
Yup, I think its a firefox+google thing. It happens on the windows firefox version too, so it has nothing to do with gdesklets. Removing the %u in the starter bar icon for firefox gets rid of it though.

---

### Post by arrizaba on 2005-05-10
hi!

thank you guys! 
removing the %u works for me!

---

### Post by ZephyrXero on 2005-08-10
It is definitely something to do with the gDesklets/Starter Bar. This was really freaking me out too till I read this and a couple other threads. I tried opening Firefox from the Gnome applications menu and it worked just fine. I checked the launcer and it has the %u. Then I took the %u off my gDesklets starter bar and it's working fine now too. You'd think the guys who write the starter bar would have noticed such an obvious bug by now :(

---

### Post by TristanMike on 2005-08-10
That's funny cause I have the %u and my Firefox starts up just fine to whatever page I set it too.

---

### Post by egon spengler on 2005-08-10
[QUOTE=tread]Yup, I think its a firefox+google thing. It happens on the windows firefox version too, so it has nothing to do with gdesklets. Removing the %u in the starter bar icon for firefox gets rid of it though.[/QUOTE]


Re-read [ssam's post](http://ubuntuforums.org/showpost.php?p=149103&postcount=7). It isn't a starterbar bug, it's the way that firefox works. If you enter "firefox %u" in the cli or create a new launcher with "firefox %u" I guarantee it will go to the same university web page

---

### Post by ZephyrXero on 2005-08-11
Then how come there's no problem with the default Hoary install? The built in launcher for it has the %u command...

---

### Post by Jmonti on 2005-09-13
This is someone pushing traffic to that site, plain and simple. Just be happy its a collage site and not a page that installs a root kit!  :-P 

When it happened to me I was reminded of the good 'ol windows days... :roll:

---

### Post by mlomker on 2005-09-13
Are you guys using the U of M's mirror as your repository?  I wouldn't be surprised if their IT department has done some customizing for their users.

I use their repo because I live in the Twin Cities.

---

### Post by Jmonti on 2005-09-14
[QUOTE=mlomker]Are you guys using the U of M's mirror as your repository?  I wouldn't be surprised if their IT department has done some customizing for their users.

I use their repo because I live in the Twin Cities.[/QUOTE]

Not that I'm aware of. I only use those included in the starter guide.

---

### Post by k16 on 2005-09-14
[QUOTE=Jmonti]This is someone pushing traffic to that site, plain and simple.

[/QUOTE]
No it's not. Firefox is treating %u as a url thats all. Just launch firefox and type %u in url field and press enter. It takes you to the same page. It's just the way firefox works. If it doesn't find the url entered, it does a google search for that string and returns the first page (or the "i'm feeling lucky" page). If you're still not convinced just launch google on some other browser and search for "%u" and press "i'm feeling lucky". As explained earlier it's similar to the incident of a typo (http; ) in the url taking the user to microsoft.com.   :)

---

### Post by Jmonti on 2005-09-15
[QUOTE=k16]No it's not. Firefox is treating %u as a url thats all. Just launch firefox and type %u in url field and press enter. It takes you to the same page. It's just the way firefox works. If it doesn't find the url entered, it does a google search for that string and returns the first page (or the "i'm feeling lucky" page). If you're still not convinced just launch google on some other browser and search for "%u" and press "i'm feeling lucky". As explained earlier it's similar to the incident of a typo (http; ) in the url taking the user to microsoft.com.   :)[/QUOTE]

Yes, you are right. I tried it out and went the site even on windows. Hopefully this will be fixed in the next StarterBar release.  :smile:

---

### Post by rama on 2005-09-15
[QUOTE=Jmonti]Yes, you are right. I tried it out and went the site even on windows. Hopefully this will be fixed in the next StarterBar release.  :smile:[/QUOTE]
 So what does %u stand for. I can see it in most shortcuts I have for many apps.

---

### Post by Jmonti on 2005-09-19
If I understand it correctly, the % tells google to search "I'm feeling lucky" and the next letter or word is what to search for.

---

