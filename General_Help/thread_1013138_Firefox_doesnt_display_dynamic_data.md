---
title: "Firefox doesnt display dynamic data"
date: 2008-12-16
forum: General Help
---

### Post by xXJT-JaredXx on 2008-12-16
just wondering if there is something that can allow Firefox to display dynamic data as the only browser that i have got to do this is Internet Explorer (on Windows).

Thanks for any help.

---

### Post by kanikilu on 2008-12-16
Can you clarify what you mean by "dynamic data"? Is there a link to a page you can provide as an example of what works on IE and not on FF?

---

### Post by xXJT-JaredXx on 2008-12-16
i'm using it to display data from a machine (peer to peer) and using a browser to display information and FF does not display the live data

---

### Post by Nonno Bassotto on 2008-12-16
What is the output of your p2p program? An html with javascript? Maybe it would be simpler if you told us what program you are using.

---

### Post by xXJT-JaredXx on 2008-12-16
jus using an ethernet network i am loging onto a machine to view data and by using IE it will display all static and dynamic but if i use FF it will only display the static data and as far as i know it is java and i have the java installed and working on FF

---

### Post by jamesstansell on 2008-12-16
> **xXJT-JaredXx said:**
> jus using an ethernet network i am loging onto a machine to view data and by using IE it will display all static and dynamic but if i use FF it will only display the static data and as far as i know it is java and i have the java installed and working on FF

If you visit [http://browserspy.dk/plugins.php?detail=1](http://browserspy.dk/plugins.php?detail=1) with Firefox what does it show for the java plugin?

Also, do you know if you have a 64-bit Firefox or not?

---

### Post by xXJT-JaredXx on 2008-12-17
according to browserspy it does have java and if you look in the plugins java is there . . a few people have tried and had the same problem and i dont think it is 64-bit not 100% sure, its just the standard one you download

---

### Post by kanikilu on 2008-12-17
I tend to think this has something to do with the java plugin versus the browser, but since you mention IE, you obviously have access to Windows. Have you tried to see if Firefox on Windows does the same thing as on Ubuntu?

```
about:plugins
``` in the Firefox address bar should give you some basic information about the java version you're using.

---

### Post by xXJT-JaredXx on 2008-12-17
it is on a windows laptop, i'v checked everything with the java and it all seems fine and the java works on everything else, other browsers all seem to have the same problem except IE, i'v tried using FF with the IE rendering and that doesnt even work

---

### Post by mbeach on 2008-12-17
perhaps the site you are visiting is using some variant of vbscript?  Just a thought.  Can you provide a link?

If you hit F5 or refresh does the data reload correctly, or it is it not updating where IE updates on some regular interval?

Perhaps you should obtain the firebug addon for firefox and see if there are any errors being reported.  Quite possibly the site you are using was tested only with ie, and subsequently has some code that doesn't work with other browsers.  This would seem to be case since you said "other browsers all seem to have the same problem".

---

### Post by xXJT-JaredXx on 2008-12-17
i'll try the firebug addon but it isnt a website, i'm using it to display data on a machine

---

