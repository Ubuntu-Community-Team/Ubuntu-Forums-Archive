---
title: "Annoying post previews in tootips"
date: 2008-10-25
forum: Forum Feedback &amp; Help
---

### Post by Yashiro on 2008-10-25
Please add an option to disable the 'post previews' that pop up in a tootip when you hover over a topic title on the main index.

It's incredibly annoying and not something most forums ever implement.

---

### Post by LaRoza on 2008-10-25
That is a browser feature, not the feature of the forum.

---

### Post by pp. on 2008-10-26
In the forum page, each thread is rendered as table data item. One of the attributes is "title", and the value of that attribute is part of the text of the first post of the thread.

My browser displays that text when hovering over the link to the thread.

I think we can safely assume that OP wants the title attribute to be dropped from the <td> element.

---

### Post by Rhubarb on 2008-10-26
I personally like that feature, but for some threads I can't read as fast as I'd like to before the tooltips goes away ... time to see if it's something I can set for a longer period in about:config ...

---

### Post by kaibob on 2008-10-27
I've always disliked the tooltip previews and have raised this issue in a few threads. I can't recall who, but one of the moderators suggested that I keep the cursor to the side of the screen if the tooltips bothered me. I did a google search to see if there was some way to entirely disable tooltips in Firefox but couldn't find anything. So, I think we're out of luck on this one.

---

### Post by Yashiro on 2008-10-27
> In the forum page, each thread is rendered as table data item. One of the attributes is "title", and the value of that attribute is part of the text of the first post of the thread.Indeed. It's not funky browser workings, it's more abuse of the 'title' attribute to generate a post preview.

It is irritating and probably puts unnecessary load on the server.

---

### Post by mips on 2008-10-27
+1 Another that finds it annoying.

---

### Post by LaRoza on 2008-10-27
> **Yashiro said:**
> Indeed. It's not funky browser workings, it's more abuse of the 'title' attribute to generate a post preview.

It isn't abuse of it. I find it helpful. Of course, when I see it, I don't get it so big, because I use Opera.

> 
It is irritating and probably puts unnecessary load on the server.
No...

---

### Post by Yashiro on 2008-10-27
You see this is why I suggest it become an option. 
Like everything some people will like it, some won't.

If you say the extra page size is not an issue then ok, but the pop up irritation remains.

---

### Post by Yashiro on 2008-10-27
forum time out, double post. :)

---

### Post by LaRoza on 2008-10-27
> **Yashiro said:**
> You see this is why I suggest it become an option. 
Like everything some people will like it, some won't.

If you say the extra page size is not an issue then ok, but the pop up irritation remains.

If your browser can be configured to change that behavior, I suggest you try that ;)

vBulletin is commercial software and editing it is possible, but it can really mess it up (and I don't think we are going to configure the forum around people's preferences)

---

### Post by kaibob on 2008-10-27
I placed the following in the userChrome.css file, and it seems to supress all Firefox tooltips:

```
tooltip {
  display: none !important;
}
```

REFERENCES:

[http://forums.mozillazine.org/viewtopic.php?f=40&t=660337](http://forums.mozillazine.org/viewtopic.php?f=40&t=660337)

[http://kb.mozillazine.org/UserChrome.css](http://kb.mozillazine.org/UserChrome.css)

---

### Post by smartboyathome on 2008-10-27
> **kaibob said:**
> I placed the following in the userChrome.css file, and it seems to supress all Firefox tooltips:

```
tooltip {
  display: none !important;
}
```

REFERENCES:

[http://forums.mozillazine.org/viewtopic.php?f=40&t=660337](http://forums.mozillazine.org/viewtopic.php?f=40&t=660337)

[http://kb.mozillazine.org/UserChrome.css](http://kb.mozillazine.org/UserChrome.css)

Or, you can just use stylish to do that. ;)

---

### Post by issih on 2008-10-27
I'd cry if that feature went away, it makes it much easier to see if reading the thread will be worth the effort. Each to their own I guess..

---

### Post by Yashiro on 2008-10-29
[COLOR="RoyalBlue"]browser.chrome.toolbar_tips false[/COLOR] works for Firefox. It applies instantly so can be toggled on/off.

---

### Post by Visible Spirit on 2008-10-31
@ Yashiro,

Thank you for the tip! Those darn pop-ups were MOST annoying when trying to simply read the titles and moving the mouse across the page or scrolling it.

Regards,
Visible Spirit

---

### Post by Elfy on 2008-11-01
Personally I find it really useful - an easy way to find out what threads are about when the thread title is 

> i think ive broke itor  > Newb questions redux or > oh newbie error help please.

---

### Post by Visible Spirit on 2008-11-01
> **forestpixie said:**
> Personally I find it really useful - an easy way to find out what threads are about when the thread title is

Quote:
i think ive broke it

or

Quote:
Newb questions redux

or

Quote:
oh newbie error help please.

Very good points forestpixie.

If there is any way this could be implemented as a feature for members to turn on or off in CP on the forum side, that would be a welcome option for those that aren't interested in the balloon pop-ups.

Another option / idea (and possibly better all the way around), could be to limit the area on the index boards that triggers the pop-up to an icon, ...rather than the entire area of the title. This way one could trigger the titles of interest without the annoying effect of the large pop-ups as you run your mouse across the page or scroll with the keyboard, leaving the cursor stationary which triggers each title as it passes blocking the view of the next title in-line for the viewer. This is what I find annoying about it personally because many times I will scroll with the keyboard when looking for something and don't like the idea of each title description popping up, thus having to be distracted and stop to move the cursor off the page to avoid this annoyance.

Over the years I've seen both options in use on various forum boards. It just makes sense to limit this in some fashion so all can be happy. Isn't that what debates are all about? To come to a happy medium for all (or at least the majority)? How much effort this would be I'm not sure because I'm not a programmer by anyone's stretch of imagination. But I can't imagine it's impossible, simply because other forums have implemented these concepts and they work.


Regards,
Visible Spirit

---

