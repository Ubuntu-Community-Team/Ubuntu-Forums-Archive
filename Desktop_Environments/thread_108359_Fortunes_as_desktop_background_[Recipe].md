---
title: "Fortunes as desktop background [Recipe]"
date: 2005-12-25
forum: Desktop Environments
---

### Post by runlevel0 on 2005-12-25
I have been trying to figure out how to display text on the background, specially fortunes (bofh-excuses).

(Find Ingredient list below)

A guess was kwebdesktop, a program that you can call from "configure desktop > advanced options". This program invokes an URL that is displayed to the background. Thus the only thing we need is something to parse the output of *fortune* and add HTML tags. This application exists, of course, it's *txt2html* and it has a pretty huge set of options. Just refer to the man page to see all of them. Two of these options are useful for my purposes: --outfile FILENAME --style_url PATH.

So, now we have all what we need, except the CSS file. I wanted fat text, more or less centered... So, once I was ready with the CSS I just wrote a script to invoke fortunes and pipe it through txt2html.

I use a ~/etc directory where I store local stuff, so I placed the style sheet there and pointed txt2html to write the output file in this same dir.

The next to do was starting Kcron and puttin my script into my crontab so that it executes every hour.

The next step is to open "desktop configuration > advanced" , enabling the applications, choosing "kwebdesktop" and changing the URL to point to my local file.

Once ready I disabled the desktop wallpaper to see if everything went OK, and played around with the blending options until I found one  I liked.

That was all. Now I get a new BOFH-excuse every hour written onto my desktop and without the annoying side effects of Karamba (like windows sinking below the karamba display).

[b]Ingredients list[b]
[list]
[*] text2html
[*] kcron
[*] an editor of your choice
[/list]

I uploaded the files as an example, but keep in mind that the paths have not been changed (!). The script has been renamed with a txt suffix so that the upload system accepts it (it's a oneliner).

You can of course render what you want, as long as txt2html can render it. You could also pipe the text output through *troff * prior to piping it through txt2html... 
Now an open question: Is there any other, more direct way of rendering text to the root window?

---

