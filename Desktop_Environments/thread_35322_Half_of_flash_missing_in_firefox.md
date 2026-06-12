---
title: "Half of flash missing in firefox"
date: 2005-05-18
forum: Desktop Environments
---

### Post by mrscintilla on 2005-05-18
Is it a known problem that flash pages miss the right half display in firefox?
This happens to both my firefox 1.02 and 1.04.

I ran the automated script and got flash pluggin for firefox. I don't know how it set the flash up.
I also got the mozplugerrc thing in /etc/mozpluggerrc, but I don't think that has much to do with flash.

the system is 32-bit ubuntu 5.04.  the video driver is the nvidia one in the repository.

---

### Post by not_yet on 2005-05-18
set up flash as follows

[http://plugindoc.mozdev.org/linux.html#Flash](http://plugindoc.mozdev.org/linux.html#Flash)

works fine here :)

---

### Post by jeremy on 2005-05-19
The instructions you refer to are;
   1. Download Flash Player 7.0.
   2. Decompress it, then copy libflashplayer.so to your Mozilla plugins directory and flashplayer.xpt to your Mozilla components directory.

Are these dirs ~/.mozilla/firefox/plugins & ~/.mozilla/firefox/components respectively?

---

### Post by not_yet on 2005-05-19
> Are these dirs ~/.mozilla/firefox/plugins & ~/.mozilla/firefox/components respectively?

yes :)

---

### Post by jeremy on 2005-05-19
Nah, doesn't make any difference, firstly, the correct dirs are in fact; ~/.mozilla/plugins & ~/.mozilla/components
But having sorted that one out, some sites still only show half a page, an example is [www.andyfoulds.co.uk](www.andyfoulds.co.uk)
It would appear to be a bug in the html where the size of the flash is expressed as 100% rather than in pixels.

---

### Post by vanaedium on 2005-05-19
I have the same problem with 
[www.terotero.com](www.terotero.com)
And I think there's no solution actually.
If someone know something please help us!!! ](*,)

---

### Post by darkaudit on 2005-05-19
I've had flash working fine... mostly. At least ESPN.com isn't complaining that it's can't find flash.

But go somewhere like speedtv.com, and it's complete crap.

Put it all down to incompetent web design. *They* are the ppl who should have to fix things. :)

---

### Post by jeremy on 2005-05-19
I have done a few experiments, and can confirm that (as I said in my previous post) there is a bug when in the html the size of the flash is expressed as 100% rather than in pixels.
Whether this is actually a bug, or if it is that declaring the size as a percentage is incorrect (but tolerated by some systems/browsers), I do not know.

---

### Post by jeremy on 2005-05-19
Bloody annoying, anyway!

---

### Post by rum beverage on 2005-05-22
just wondering if anyone ever found a way around this?

---

### Post by jeremy on 2005-05-23
I have been trying for months, the closest I have come is, when I come across the problem, to look at the source code of the page, and navigate directly to the flash file.
That then loads at the full browser size.

---

### Post by Rlink on 2005-05-28
[QUOTE=jeremy]I have been trying for months, the closest I have come is, when I come across the problem, to look at the source code of the page, and navigate directly to the flash file.
That then loads at the full browser size.[/QUOTE]
Thanks a lot for this, it will have to do for now. But instead of searching through source code for a URL to the flash, heres a simpler method:

1. Go to your bookmark manager in Firefox. (Bookmarks>Manage Bookmarks)

2. Create a new bookmark. (File>New Bookmark)

3. Put whatever you'd like in the name box, and in the location box, put this, exactly as it appears:
```

javascript:s='';b=0;while(document.embeds[b]){s+='<a href=%22'+document.embeds[b].src+'%22>'+document.embeds[b].src+'</a><br>';b++;};if(s){document.write(s);document.close();}else{alert('Sorry, no embeds found.');}

```

and click OK.

4. Go to the page in question where the flash is screwing up, click on Bookmarks, and then click on the bookmark you just made. The bookmark will search the source for you for any embedded files and list them for you. All you need to do now is click on the appropriate flash file.

Thats a lot easier than searching through the source file, right?

---

### Post by graigsmith on 2005-05-28
> **Rlink]Thanks a lot for this, it will have to do for now. But instead of searching through source code for a URL to the flash, heres a simpler method:

1. Go to your bookmark manager in Firefox. (Bookmarks>Manage Bookmarks)

2. Create a new bookmark. (File>New Bookmark)

3. Put whatever you'd like in the name box, and in the location box, put this, exactly as it appears:
```

javascript:s='' said:**
> ){s+='<a href=%22'+document.embeds[b].src+'%22>'+document.embeds[b].src+'</a><br>';b++;};if(s){document.write(s);document.close();}else{alert('Sorry, no embeds found.');}

```

and click OK.

4. Go to the page in question where the flash is screwing up, click on Bookmarks, and then click on the bookmark you just made. The bookmark will search the source for you for any embedded files and list them for you. All you need to do now is click on the appropriate flash file.

Thats a lot easier than searching through the source file, right?

[http://www.iriver.com/html/index.asp](http://www.iriver.com/html/index.asp)

this worked for iRiver's site :)

somebody deserves a genius award :)

---

### Post by jeremy on 2005-05-29
That is a great work around, thanks.

---

### Post by angkor on 2005-05-29
Very Nice!! Thanks.

---

### Post by greenwom on 2005-06-18
IS there anything in the works to correct these problems in Mozilla?
Is this a Linux/Ubuntu problem or a browser problem?

---

### Post by der_joachim on 2005-06-19
[QUOTE=greenwom]IS there anything in the works to correct these problems in Mozilla?
Is this a Linux/Ubuntu problem or a browser problem?[/QUOTE]

It is most definitely a browser problem. I had the same problem in Debian Woody and Mandrake 10.X. The only thing that helped for me was to create an entirely new profile. Hardly a good solution, is it?  ;-)

---

### Post by stepore on 2005-06-21
[QUOTE=Rlink]Thanks a lot for this, it will have to do for now. But instead of searching through source code for a URL to the flash, heres a simpler method:
...

Thats a lot easier than searching through the source file, right?[/QUOTE]

awesome; cheers.

another option -- at least it works for me is to fire up the 'konqueror browser'. it seems to display all those mozilla-half-page-flash-sites in full screen. don't know why, but it seems to work if your firefox is not.

---

### Post by jeremy on 2005-06-21
Yes, my konq works too, but I prefer firefox.

---

