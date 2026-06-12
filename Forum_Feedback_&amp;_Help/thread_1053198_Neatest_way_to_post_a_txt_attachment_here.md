---
title: "Neatest way to post a txt attachment here?"
date: 2009-01-28
forum: Forum Feedback &amp; Help
---

### Post by 2CV67 on 2009-01-28
**Edit: This has since evolved to include posting images too.**

Hi all!

This is not a big concern, just curiosity.

I wanted to attach my menu.lst file contents to a post on this forum.
I opened it in gedit & copied it to my desktop where it sat looking like a text file (with no .suffix though...)

When I tried to attach it to my post, I got an error message about illegal file type, or something similar.
That was when I noticed it didn't have a .suffix.

I then pasted it into OpenOffice Writer & saved it as an .odt file.
When I tried to attach that, it exceeded the max size allowed for that file type.

Finally it dawned on me that I could save it as a .txt file from OOo so that was OK.

Is that the best way to get from gedit to an attachment for this forum, or is there a simpler way?

---

### Post by birddog165 on 2009-01-28
I just click on the quote button in the online message box and do a copy/paste of the "guts" of the file inbetween the word tags QUOTE and QUOTE.

Like this:
> Hi I'm a program code

---

### Post by birddog165 on 2009-01-28
There's probably a better way, but I don't know it yet ;)

---

### Post by ibuclaw on 2009-01-28
[http://paste.ubuntu.com](http://paste.ubuntu.com)

Regards
Iain

---

### Post by unutbu on 2009-01-28
Along the same lines as tinivole's suggestion, there is this command:
```
sudo apt-get install pastebinit
pastebinit -i /boot/grub/menu.lst -b http://paste.ubuntu.com
```
It sends /boot/grub/menu.lst directly to paste.ubuntu.com and returns the url of where you can find it.

---

### Post by Locke_99GS on 2009-01-28
Or you could wrap the contents in *[noparse]```
 ... 
```[/noparse]* tags in the forums here. The results being like this:

```

This is text
I could have copied and psted this from my menu.lst or any other text file.

```

For attaching, if the file were on your desktop and you wanted it to have the *.txt* extension, you could right-click the file, go to rename, and add an extension. Likewise, you could change the filename from the terminal:

```

mv ~/locke/Desktop/myFile ~/locke/Desktop/myFile.txt

```

And sent it as an attechment, though I can tell you that myself (and most others, I'd reckon) prefer to see the contents of a file inline with a post here, wrapped in *CODE* tags. It's one less step we have to go through to examine the file.

---

### Post by 2CV67 on 2009-01-28
> **Locke_99GS said:**
> Or you could wrap the contents in *[noparse]```
 ... 
```[/noparse]* tags in the forums here. The results being like this:

```

This is text
I could have copied and psted this from my menu.lst or any other text file.

```


....I can tell you that myself (and most others, I'd reckon) prefer to see the contents of a file inline with a post here, wrapped in *CODE* tags. It's one less step we have to go through to examine the file.

OK, that makes sense.
Overall it's a cleaner, simpler method.

Thanks for so many good responses to a tiny question!

---

### Post by Iowan on 2009-01-28
If it's a text-type file (like smb.conf or your menu.lst) I save a copy where I can find it easily, then rename it with a .txt on the end eg. smb.conf.txt.

---

### Post by 2CV67 on 2009-02-11
Supplementary question:

How to include an image inside the text, rather than as an attachment?

I saw somewhere that you should upload to a site like [http://www.imagehosting.com/](http://www.imagehosting.com/) then paste a reference to it in the "insert Image" box.

Is that right?
Is it encouraged (within reason...).
Is that the best site?

Any other comments?

Thanks!

---

### Post by Achilles124 on 2009-02-11
Again, very simple. Add a picture to a site (say:Flickr). Then copy the url and then paste the url into your message.
Any site will do as long as they keep your image for a period of time.

Easy does it.

---

### Post by unutbu on 2009-02-11
Tip: If you see a post with some interesting effect, click the quote button. You will see the codes used to generate the effect.

[How to display images inside a post](http://ubuntuforums.org/showpost.php?p=5241145&postcount=31)
[A list of codes that can be used in posts](http://ubuntuforums.org/misc.php?do=bbcode)
[Guide to Forum features](http://ubuntuforums.org/showthread.php?t=1006656)

---

### Post by 2CV67 on 2009-02-11
Thanks both!

Unutbu, you certainly know how to pack & lot of useful information into a short post!

I am embarrassed that I searched the forum & Googled for ages without finding those links...

So, basically, it is not possible to simply attach an image from my PC (like I can to the bottom of the post) & arrange for it to be visible within the text?

The BB Code list mentions > The [attach] tag allows you to display an attachment in your post rather than at the bottom. It will only display attachments that belong to the post in which it is utilized.
But that is not usable here?

As an aside, the French ubuntu Forum has a special "Ephemeral" section where you can try out your skills (or lack of) at posting without spoiling any useful threads and they wipe it all out after a time.
That's a good idea I have not found here (but maybe I just didn't look enough yet)...

Thanks again!

---

### Post by unutbu on 2009-02-11
Thank you for telling me about the [attach] BB code... I didn't know about that.

As far as I know, there is no direct way to embed an image from the machine into a post. When I really want to do that, I find that I need to 

[list]
[*]first attach the image
[*]submit the post
[*](in firefox) right-click on attached image, type 'a' to copy the link location
[*]edit the post
[*]Use [img] tags to embed the image, or now even better, use [attach] tags to embed the attachment.
[/list]

As an example, here is the short-cut button to insert [img] tags in a post:
[attach]102961[/attach] (It's the one which looks like a postage stamp of a mountain.

---

### Post by 2CV67 on 2009-02-11
Before I started playing with Ubuntu, I would have called that tortuous. ;)
[attach]102962[/attach] [attach]102963[/attach]
Let me have a dummy run at putting a dummy image above this line.

---

### Post by 2CV67 on 2009-02-11
OK - that works then. (1st image)

You can even upload the image during the edit if you need/want. (2nd image)

That is exactly the result I was looking for.

> **Locke_99GS said:**
> ....I can tell you that myself (and most others, I'd reckon) prefer to see the contents of a file inline with a post here, wrapped in *CODE* tags. It's one less step we have to go through to examine the file.

I completely agree with Locke 99GS on this, now I have had time to think about it, and the same logic holds for many small images (screenshots etc) which are more conveniently dealt with if they are embedded in the text.

Is there any good reason that this facility is not included on the forum?

Should it be?

---

### Post by bapoumba on 2009-02-11
Moved to FFH.

@ 2CV67: nice car, sweet memories ;)

As far as uploading files, there is an option, but not all file formats are supported. You can upload : bmp bz2 deb doc gif gpl gz jpe jpeg jpg odg odp ods odt pdf png psd py sh svg tar txt xcf zip.

---

### Post by 2CV67 on 2009-02-11
> **bapoumba said:**
> 
@ 2CV67: nice car, sweet memories ;)
Not only memories - mine still runs...

And I can insert it here:
[attach]102989[/attach]
without editing. :D

---

### Post by 2CV67 on 2009-02-11
OK, building on everything you all said previously….

**_To insert an image in your text instead of below_**:

Copy/paste [attach][/attach] into your text where you want the image.

Go through the usual procedure to upload your image as an attachment.

Find your image, either in the "Manage attachments" window or by scrolling down in your post to "Additional Options" > Attach files.

Right click.
Look in properties.
Select the id (in the example below, it's 102990)
Example //ubuntuforums.org/attachment.php?attachmentid=102990&stc=1&d=1234385747
Copy that number.

Paste it into [attach][/attach] .

Job done!

Thanks everybody!

---

### Post by 2CV67 on 2009-02-11
No - it's easier than that:

Upload attachment in usual way.

Right click on attachment as above.

Select "Copy link location" as Unutbu said.

Go to your post & click on "Insert Image".
This opens a dialogue box asking for url.
Paste in the complete "Copy link location" you just copied.

Didn't even hurt!

---

### Post by hyper_ch on 2009-02-12
you could just add the .txt file extension and then you could have uploaded it easily.

Edit: Didn't see there was a second page ;)

---

### Post by 2CV67 on 2009-02-13
Excuse me - this is just a dummy post.

I was trying inserting images & looked at 'preview post' where the image is way too big.

I want to see what it looks like when posted.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=103214&stc=1&d=1234541465[/IMG]

The end.

---

### Post by 2CV67 on 2009-02-13
Hmmm...

The posted image is 23% bigger than the original, seen on the same screen.

Why would that be?

How to correct it (without jumping through too many hoops)?

---

### Post by Elfy on 2009-02-13
Personally I prefer to see images as attachments - then I can look if I want and aren't forced to do so - and if I was unlucky enough to have dialup then I would be not happy about having to download images people put in threads.

---

### Post by 2CV67 on 2009-02-13
> **forestpixie said:**
> Personally I prefer to see images as attachments - then I can look if I want and aren't forced to do so - and if I was unlucky enough to have dialup then I would be not happy about having to download images people put in threads.

Good point!

Thanks!

---

### Post by bapoumba on 2009-02-13
Have you seen that sticky thread, 2CV67?
[http://ubuntuforums.org/showthread.php?t=1006656](http://ubuntuforums.org/showthread.php?t=1006656)

---

### Post by 2CV67 on 2009-02-14
> **bapoumba said:**
> Have you seen that sticky thread, 2CV67?
[http://ubuntuforums.org/showthread.php?t=1006656](http://ubuntuforums.org/showthread.php?t=1006656)

Yes, of course I have read the stickies ;) but thanks for asking!
In fact the contents of the 2 items on attaching & posting images are etched on my retina but I still have not fully understood & am not satisfied with my results yet.
I would quite like to beat this subject to death, while we are here...

From the stickies:
Aysiu's post 'How do I attach an image to my post?' covers basic attaching of your own images to a post.
Images are limited in size, for example 19.5 KB for .bmp & 976.6 KB for .jpeg
Images will appear attached to the bottom of the post, which you may or may not want.

LaRoza's post 'Posting Images on the Forum' covers more advanced stuff, like importing images from the web and uploading your own images bigger than the size limit shown.
This involves uploading to a third-party hosting site & using thumbnails.
Size not a problem.
Images can be embedded in your text using the 'Insert Image' icon.
In that post, the desktop image appears, full size, in the post, with an apparently redundant thumbnail at the bottom, taking up space & allowing you to get a full size copy, which you already have...
The hosted image appears inset in the text, rather than as an attachment at the bottom...
If you click on it, you go to the host site.

Going through third-party sites like imagehosting is a pain - I avoid that kind of site which keeps throwing up pop-ups & heaven knows what else.
Several people here seemed convinced that you need to go via third-party host sites even to embed you own images in your text, but we found out on this thread that is not true.

I started this thread asking how to attach text files, but was easily convinced it was more efficient for readers if the text was inserted in the post rather than attached at the bottom.
I thought, & still think, the same is often true for images, if they are illustrating a problem or illustrating a How-To.
LaRoza's Official Guide Post more or less recommends inserting images in your text if you want to, but respected ForestPixie throws up a problem for dial-uppers I had not thought about & don't fully understand.
What is the best guideline?

In posts #14 & #17, I managed to insert little (thumbnail?) images in the text, which you can click on if you want, to open bigger images.
Without visiting hosting sites.
**_I think that is the result I would often like to have._**

In post #21 I did almost the same thing, but ended up with an oversize image inserted in the text & a redundant thumbnail at the bottom - certainly not a good result.

I think I know what I did differently & am re-testing, but nothing here is very obvious or clear!

So - further discussion, clarification & experimentation welcome!

---

### Post by 2CV67 on 2009-02-14
OK - I found out how to do it (not how I did it yesterday...).

Upload your image directly to the ubuntu site as usual (within size limits).

Put the cursor where you want the image.

Click on 'Attachments'

Click on the image you want to put there:
[ATTACH]103348[/ATTACH]

...and there it is, as an embedded thumbnail you can click on to get a bigger image if you want.
...without going near an outside hosting site.

I think that is the result I wanted & it's very straightforward when you have found it & I think it should not upset dial-uppers. :D

But it isn't explained anywhere  :(

---

### Post by bapoumba on 2009-02-14
> **2CV67 said:**
> 
But it isn't explained anywhere  :(
I did not know we could do it that was, learning new things everyday.
I've edited the "Guide to Forum features" to link to your post. Now it is ;)

---

