---
title: "mozilla-acroread plugin not working"
date: 2006-10-06
forum: Desktop Environments
---

### Post by kikinovak on 2006-10-06
Hi, I just installed acroread and mozilla-acroread on Xubuntu 6.06, but the plugin doesn't seem to work. Opening Firefox on the "about:plugins" page only shows Flash and Java, but no trace of Acroread. I also tried this on another install of Ubuntu 6.06, to no avail.

File a bug report? Or did I overlook something?

---

### Post by guysmiley25 on 2006-10-06
I am too having the same problem. Also using xubuntu. I did have it working in kubuntu though.

If you find a solutions please post.

---

### Post by guysmiley25 on 2006-10-11
Anyone?

---

### Post by guysmiley25 on 2006-10-21
Ok so here is a solution that is great for xubuntu. but not really the ideal solution for the problem.

Ok so this is the situation. xubuntu comes with a pdf viewer already called evince. The problem! is does not embed itself into firefox. And that's why (at least in my case) we remove that and install acrobat. But this hasn't been working with xubuntu for me and others either.

Solution. Remove acrobat stuff reinstall evince, and make it work with firefox.

Ok First up Remove acrobat stuff.
```
sudo apt-get --purge remove acroread mozilla-acroread acroread-plugins
```
Now lets reinstall evince. Ok now here's the thing I said that evince already comes with xubuntu, however if you did not remove it then you still have to do this part becasue xubuntu comes with evince-gtk, and what we need is evine. Ok so I lied.```
sudo apt-get install evince
```.

Ok now where going to do the bit where we make evince work in firefox. First install mozplugger. ```
sudo apt-get install mozplugger
```.
Now ```
sudo mousepad /etc/mozpluggerrc
```.

And find where is says this
```

application/pdf: pdf: PDF file
application/x-pdf: pdf: PDF file
text/pdf: pdf: PDF file
text/x-pdf: pdf: PDF file
```
and this
```

application/x-postscript: ps: PostScript file
application/postscript: ps: PostScript file

```

Add add this line under them
```

repeat noisy swallow(evince) fill: evince "$file" 

```

Here is mine for an example
```

application/pdf: pdf: PDF file
application/x-pdf: pdf: PDF file
text/pdf: pdf: PDF file
text/x-pdf: pdf: PDF file
	repeat noisy swallow(evince) fill: evince "$file"

```
and
```

application/x-postscript: ps: PostScript file
application/postscript: ps: PostScript file
	repeat noisy swallow(evince) fill: evince "$file"

```

Hope that helps. PS there was other lines of stuff like that for me I just commented them out.

Tip: You can see what plugins your have in firefox by going to about:Plugins in the address bar.

---

### Post by SebMKd on 2007-04-29
Hi GuySmiley25,

I had, I believe, installed everything on my Dapper for Firefox 2.0 to open PDF with acroread-plugin, but it never worked.
So here I am trying your suggestion and the following command is not found:
sudo mousepad ...

I'll make some research about mousepad, but I'm hoping you'd respond sooner that I'm done searching :)

Thanks!

---

### Post by jms830 on 2007-05-01
replace **mousepad** with **gedit**

---

### Post by SebMKd on 2007-05-03
Interestingly enough, without editing anything I can open PDF in Firefox now...

And, of course, gedit! I should have thought about it...

Thanks though

---

