---
title: "Php Pages Hang - Browser Independent"
date: 2009-05-07
forum: General Help
---

### Post by ajacx on 2009-05-07
Around mid March I installed 8.04 on a desktop and upgraded to 8.10. I was not able to use certain websites satisfactorily after that including, but not limited to, wordpress.com, ubuntuforums, yahoo mail and several others. I noticed that the webpages usually hang when I try submitting something, and usually after I was able to login to the site. This was all on firefox, so I tried a few other browsers: Opera, Epiphany, Seamonkey all to no avail.

Since I was essentially using ubuntu for development, and it was a dual boot, I ended up logging into windows when I wanted to use those websites, hoping that whatever it was would be fixed I upgraded to 9.04. Unfortunately that hasn't happened and I'm frustrated with this experience and will most probably re-install over the weekend when I get the new LiveCD. This seems to have worked for someone else who had this problem: [http://ubuntuforums.org/showthread.php?t=1122877](http://ubuntuforums.org/showthread.php?t=1122877)

But since it has piqued my curiosity, I'd like to figure out what is going on (and of course avoid an unnecessary re-install if possible). Is it a backend problem with the gecko engine? Is there a way to re-install the gecko engine, or is it something completely different.

Another thing is I have installed an apache server for development purposes only. The php pages on my mini project seem to work fine, even when a new session has been created - unlike the experience via the internet when the pages I mentioned at the start do not work, and sometimes I am offered the chance to save the php file, which ends up being blank! Anyone got any idea on what is happening?

---

### Post by mb_webguy on 2009-05-07
Your browser doesn't see PHP (or any other server-side script) when opening a web page.  The script outputs html, no different whatsoever from any other html page, and that's what the server send to your browser.

If it's *only* when submitting forms, then I suppose that could be a big in the browser, but I don't see how it would affect multiple browsers -- particularly both Firefox and Opera, which have little to do with one another.

I don't see how it would be affecting you in the way you describe, but did you change the iptables (firewall) settings at all?

Another thing it could be is Javascript.  A lot of times forms will do some validation on the client side before submission.  Try opening Tools > Error Console (in Firefox) while at one of those websites, clear the console, then do something that normally causes the browser to hang, and see what messages pop up.

---

### Post by ajacx on 2009-05-07
Thanks for your reply mb_webguy. 
> Your browser doesn't see PHP (or any other server-side script) when opening a web page. The script outputs html, no different whatsoever from any other html page, and that's what the server send to your browser.
I don't remember saying that was the case, but its worth pointing out to you that there are instances when you can see php code, say for example when the page isn't saved as a php file on the server.

Anyway,maybe I wasn't clear, but it looks like whenever a _POST request is sent after a session starts, the page hangs, or after a long time I am given the choice of saving a filenamehere.php file of 0 bytes. And this is browser independent. I have not changed IP table settings. I shall try your suggestion and print the error messages should any arrive.

If anyone else has experienced this, or has any suggestions I'm all ears.

---

### Post by xpasi on 2010-09-22
Bit old thread but I ran into this while searching the web about my problem...

I have the same problem as described above.

Using ubuntu 10.04

I do web dev and have several pages using the same site engine (drupal) in one hosting company.

I did a site for a customer and all worked like charmed few months ago. Then there was a long pause when we didn't update their site. Now that I do some work on the site, I get this problem. Firefox, Opera, Chrome "hang" when trying to save an edited page or change any setting in the site (ie. when posting data to the server). Usually, it just ends up into a white page after several minutes of waiting with nothing saved at the site and sometimes (really rarely) it gives a timeout error.

Pages load without problem and I can log in to the site.

I have 2 PC's with 10.04 and BOTH have the exact same problem, while in Windows there is no problem.

Odd thing is that it only affects this one site. Another site using the same CMS in the same hosting server works without problems!

Will try it from another distributions live CD later today and see how things go (maybe it's a linux problem).

---

### Post by xpasi on 2010-09-22
Did some testing just now and problem persists in Links web browser too!

Small data (like a single field) can be saved in all browsers, but as soon as the data to be posted to the server grows past few fields it hangs up.

Same issue in Knoppix 6.0 and Ubuntu 9.10 ... Kernels 2.6.28 in knoppix and 2.6.31 in ubuntu. Knoppix didn't use gnome and uses some other browser which name I didn't write down.

---

### Post by xpasi on 2010-09-22
Nothing wrong with the internet connection either.

Tried it through USB modem with the same result....

---

