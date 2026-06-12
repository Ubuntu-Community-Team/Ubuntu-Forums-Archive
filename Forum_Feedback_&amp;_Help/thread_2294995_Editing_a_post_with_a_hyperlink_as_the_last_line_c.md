---
title: "Editing a post with a hyperlink as the last line creates problem"
date: 2015-09-15
forum: Forum Feedback &amp; Help
---

### Post by coldraven on 2015-09-15
If I try to edit this post by adding new text at the bottom (below the Unetbootin link) whatever I type becomes a link. e.g foobar becomes underlined.
This has happened a few times when immediately after posting I wanted to add some more information. Maybe I'm being a bit brain dead but I have not figured out how to stop this formatting. Is it just me or is it a bug?
[http://ubuntuforums.org/showthread.php?t=2294932&p=13356502#post13356502](http://ubuntuforums.org/showthread.php?t=2294932&p=13356502#post13356502)

---

### Post by coffeecat on 2015-09-15
I think what you are doing is accidentally adding the new text between the end of the link URL and the BBCode [noparse][/url][/noparse] tag which closes the hyperlink. If that is what is happening, my guess is that you are using WYSIWYG mode in the message editor. I abandoned WYSIWYG mode as more trouble than it's worth some years ago and now use Standard Editor in my General Settings -> Message Editor Interface. That way I can see the BBCode I'm using and not add edits in the wrong place, and can make sure my formatting is OK by always doing a preview before posting.

As an alternative to changing your settings, you can use the toolbar icon that looks something like [size=1]A[/size]/_A_ in the advanced message editor to toggle from WYSIWYG mode to source mode.

The forum software adds [noparse][]()[/noparse] BBCode tags around any string that starts with [http://](http://) (&#8592; !) so it's not always obvious, particularly when using WYSIWYG editor mode, that BBCode has been added to your post.

---

### Post by coldraven on 2015-09-15
@coffecat: Thanks, I never thought to look in the settings or find the toggle which would indicate that I am indeed brain dead :)

---

### Post by v3.xx on 2015-09-15
Thanks from me too :)

---

### Post by brian-mccumber on 2015-09-15
Thanks from me three, I was writing the whole post then adding links to it to keep this from happening.

---

### Post by Doug S on 2015-09-15
Thanks from me also. I came here just now to ask this same question, and was very surprised to find this thread.

---

### Post by v3.xx on 2015-09-15
WYSIWYG should come with a warning.

---

### Post by coffeecat on 2015-09-15
> **v3.xx said:**
> WYSIWYG should come with a warning.

That is a good point. It's the bane of WYSIWYG wherever you find it, whether on this forum or elsewhere. If I had £1 for every time I found that my edit was coming out in bold, italic, or some funky font effect in a LibreOffice document because I had slightly misplaced the cursor, I'd be very rich! :)

I've amended the help text which you can see under Settings &#8594; General Settings &#8594; Message Editor Interface. The default Vbulletin text was:

> When posting messages to the forums or other members, there are three interface types available to you. The simplest of these is a simple text box, while the last is a fully-fledged WYSIWYG editor, which allows you to format your text as you want it and see the results immediately.

Depending upon the capabilities of your web browser, you may not be able to use all of these options. If you experience problems when posting messages, try switching to a different interface type.

I've added this:

> Please be warned that if you use BBCode in WYSIWYG mode, it is easy to misplace edits within already typed BBCode and thus cause unwanted formatting effects. If you use BBCode you may find that either the Basic or Standard interface suits your purposes better.

Of course, that supposes that forum members will actually find the setting and then read the help note. If anyone can think of better wording, please feel free to suggest amendments.

---

### Post by flocculant on 2015-09-15
Perhaps change the default editor.

---

