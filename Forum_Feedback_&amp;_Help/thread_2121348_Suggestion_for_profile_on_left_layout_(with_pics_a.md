---
title: "Suggestion for profile on left layout (with pics and code)"
date: 2013-03-01
forum: Forum Feedback &amp; Help
---

### Post by pqwoerituytrueiwoq on 2013-03-01
Setting:
[Quick Links -> Edit Profile -> Location of Member Profile Information on Posts]("http://ubuntuforums.org/profile.php?do=editprofile#cfield_7")
Suggestion (before):
[[IMG]http://i.imgur.com/A3LaK7Kl.png[/IMG]]("http://imgur.com/A3LaK7K")
Result (after):
[[IMG]http://i.imgur.com/zakNhEyl.png[/IMG]]("http://imgur.com/zakNhEy")
CSS Code:
```
.postbitlegacy .userinfo .postuseravatar, .eventbit .userinfo .eventuseravatar {
    display:inline;
}
.postbitlegacy .userinfo .userinfo_extra {
    float:right!important;
    width:70px;
    margin-top:0;
}
.postbitlegacy .postbody, .eventbit .eventdetails .eventbody {
    min-height:230px;
}
.postbitlegacy .userinfo {
    position:absolute;
}
```
Code for firefox's userContent.css file/Stylish:
```
@-moz-document url-prefix("http://ubuntuforums.org/") {
    .postbitlegacy .userinfo .postuseravatar, .eventbit .userinfo .eventuseravatar {
        display:inline!important;
    }
    .postbitlegacy .userinfo .userinfo_extra {
        float:right!important;
        width:70px!important;
        margin-top:0!important;
    }
    .postbitlegacy .postbody, .eventbit .eventdetails .eventbody {
        min-height:230px;
    }
    .postbitlegacy .userinfo {
        position:absolute!important;
    }
}
```

---

### Post by ajgreeny on 2013-03-01
This may be a bit premature, but can you explain a bit more clearly what to do with the text in these boxes.

I have added the text from the second box you show here to my FF userContent.css file and restarted FF, but nothing has changed in the way the forum is displayed.  Do I need an add-on (stylish) for it to work?

What do I do with the text in the first box shown?  Is that an alternative addition to the same css file if I haven't got the add-on?

---

### Post by pqwoerituytrueiwoq on 2013-03-01
This is the end result, no addon required, you can use stylish if you prefer it userContent.css
```
cat ~/.mozilla/firefox/mwad0hks.default/chrome/userContent.css | head -17
@namespace url(http://www.w3.org/1999/xhtml);
@-moz-document url-prefix("http://ubuntuforums.org/") {
    .postbitlegacy .userinfo .postuseravatar, .eventbit .userinfo .eventuseravatar {
        display:inline!important;
    }
    .postbitlegacy .userinfo .userinfo_extra {
        float:right!important;
        width:70px!important;
        margin-top:0!important;
    }
    .postbitlegacy .postbody, .eventbit .eventdetails .eventbody {
        min-height:230px;
    }
    .postbitlegacy .userinfo {
        position:absolute!important;
    }
}
```

The 1st box would be for someone who wanted to update the css on the site
all that would be needed would be ctrl+f and search for the same target and change styles

---

### Post by ajgreeny on 2013-03-01
Sorry, mea culpa!  I simply forgot to rename the file from usercontent-example.css to userContent.css, so of course, it did not work.

Now renamed as needed and working properly.  Thanks for the tip.

---

### Post by mörgæs on 2013-03-01
Thanks. A suggestion like this including CSS is more than welcome.

---

### Post by Paddy Landau on 2013-03-02
> **pqwoerituytrueiwoq said:**
> Setting…
Thank you.

---

### Post by Vaphell on 2013-03-02
it would be nice to push the time to the right, and move everything else up. Another row saved. Beans probably could be next to coffe icons, i guess they are related?


i am no html guru so moved things around using margins to roughly illustrate (added to the code above)
```

    .postbitlegacy .userinfo {
        position:absolute!important;
    }
    
    .postbitlegacy .userinfo {
        margin-top:-20px!important;
    }
    
    .postbitlegacy .postdate {
        margin-left:200px !important;
    }
    
    .postbitlegacy .userinfo_extra dd:nth-of-type(3) {
        margin-top: -120px !important;
        margin-left: 20px !important;
    }
    
    .postbitlegacy .userinfo_extra dt:nth-of-type(3) {
        display: none;
    }


```

---

### Post by ajgreeny on 2013-03-03
How can I get the same effect in chromium as I do in firefox please.  I have copied the same code as I have in the FF userContent.css file to the Custom.css file in ~/.config/chromium/Default/User StyleSheets, made it executable like the userContent.css but the user info (join date, location and beans) will not sit beside the user avatar as it does in FF, so there is still a lot of wasted space in chromium.
See screenshots for difference between the two browsers.

---

### Post by pqwoerituytrueiwoq on 2013-03-03
look at the 1st line for the code in firefox
[FONT=courier new]@-moz-document url-prefix("http://ubuntuforums.org/")[/FONT]
that is most likely your issue
if you are using a userscript just use [FONT=courier new]GM_addStyle("Normal_CSS_Code_Here")[/FONT]
just use \n for a like break and \t for a tab or you can just delete them all together
how about i just attach the script (drag/drop into extensions) [http://userscripts.org/topics/113176](http://userscripts.org/topics/113176)

---

### Post by vasa1 on 2013-03-04
> **pqwoerituytrueiwoq said:**
> look at the 1st line for the code in firefox
[FONT=courier new]@-moz-document url-prefix("http://ubuntuforums.org/")[/FONT]
that is most likely your issue
if you are using a userscript just use [FONT=courier new]GM_addStyle("Normal_CSS_Code_Here")[/FONT]
just use \n for a like break and \t for a tab or you can just delete them all together
how about i just attach the script (drag/drop into extensions) [http://userscripts.org/topics/113176](http://userscripts.org/topics/113176)

Hi, Can you help me out? I'm using Google Chrome with the Stylish Extension. I've managed to get a nearly-minimal look but I'm stuck at this point ... As the image shows, I still have three rows: 
the top row has the "age of the post" at the extreme LHS and link on the extreme RHS
the second has the poster's nick with online/offline status
the third has the user title

Can you figure out a way to have this information (div.posthead and div.userinfo_noavatar) in fewer rows? I'd prefer something not involving user scripts.

---

### Post by pqwoerituytrueiwoq on 2013-03-04
i could but, i cant guarantee it will work without the code you are using already

---

### Post by Merk42 on 2013-03-04
> **pqwoerituytrueiwoq said:**
> Setting:
[Quick Links -> Edit Profile -> Location of Member Profile Information on Posts]("http://ubuntuforums.org/profile.php?do=editprofile#cfield_7")
Suggestion (before):
[[IMG]http://i.imgur.com/A3LaK7Kl.png[/IMG]]("http://imgur.com/A3LaK7K")
Result (after):
[[IMG]http://i.imgur.com/zakNhEyl.png[/IMG]]("http://imgur.com/zakNhEy")
CSS Code:
```
.postbitlegacy .userinfo .postuseravatar, .eventbit .userinfo .eventuseravatar {
    display:inline;
}
.postbitlegacy .userinfo .userinfo_extra {
    float:right!important;
    width:70px;
    margin-top:0;
}
.postbitlegacy .postbody, .eventbit .eventdetails .eventbody {
    min-height:230px;
}
.postbitlegacy .userinfo {
    position:absolute;
}
```
Code for firefox's userContent.css file/Stylish:
```
@-moz-document url-prefix("http://ubuntuforums.org/") {
    .postbitlegacy .userinfo .postuseravatar, .eventbit .userinfo .eventuseravatar {
        display:inline!important;
    }
    .postbitlegacy .userinfo .userinfo_extra {
        float:right!important;
        width:70px!important;
        margin-top:0!important;
    }
    .postbitlegacy .postbody, .eventbit .eventdetails .eventbody {
        min-height:230px;
    }
    .postbitlegacy .userinfo {
        position:absolute!important;
    }
}
```

Thanks for all this, I was debating on doin the whole beans/joindate/location to the right of the avatar. Nice someone else had the same idea. 
As for moving the signature up, does anyone feel that there needs to be more contrast for the signature so it doesn't read as part of the post or is that existing horizontal line enough?

---

### Post by Paddy Landau on 2013-03-04
> **Merk42 said:**
> As for moving the signature up, does anyone feel that there needs to be more contrast for the signature so it doesn't read as part of the post or is that existing horizontal line enough?
I sometimes read the signature as part of the post and get confused for a few moments. Is it possible to change the background colour, say to grey? Otherwise I suggest a darker and slightly thicker separator line. Another idea is to have the separator line stretch only &#8532; of the way across.

---

### Post by pqwoerituytrueiwoq on 2013-03-04
how about:
```
.signature{border-top-color:#DD4814}
```
if the divider was more visible i think it would help, an i have never seen a color stand out more than that one, lol

---

### Post by ajgreeny on 2013-03-04
> **pqwoerituytrueiwoq said:**
> look at the 1st line for the code in firefox
[FONT=courier new]@-moz-document url-prefix("http://ubuntuforums.org/")[/FONT]
that is most likely your issue
if you are using a userscript just use [FONT=courier new]GM_addStyle("Normal_CSS_Code_Here")[/FONT]
just use \n for a like break and \t for a tab or you can just delete them all together
how about i just attach the script (drag/drop into extensions) [http://userscripts.org/topics/113176](http://userscripts.org/topics/113176)

Many thanks for trying but it does not seem to work at all.  I extracted the .js file from your archive and put it in ~/.config/chromium/Default/Extensions, made it executable, and started chromium, but no good at all; everything is exactly the same with masses of wasted space; see screenshot.

What am I not getting right?  Did I completely misunderstand your instructions?

---

### Post by pqwoerituytrueiwoq on 2013-03-04
follow the instructions in the link, followed your own instructions, not what i said
probably need to rename the js file to file.user.js
drop to chrome://extensions/
[[img]http://www.zimagez.com/miniature/screenshot-03042013-044905pm.php[/img]](http://www.zimagez.com/zimage/screenshot-03042013-044905pm.php)

---

### Post by ajgreeny on 2013-03-04
[COLOR=#222222][FONT=Verdana]Thanks again, and sorry for the misunderstanding; I thought you meant me to drag the file to the extensions folder, not the web page which I have now done, and I'm almost there but not quite all the way yet.[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]My problem is that I don't understand which of the entries relates to which of the items that have been moved.  The items such as number of beans, join date and location are still too far down in the margin, and all my attempts to move them higher get me nowhere, as I can not figure out which part of the code relates to that part of the display.
Any ideas where I'm going wrong?
[/FONT][/COLOR]

---

### Post by pqwoerituytrueiwoq on 2013-03-04
```
.postbitlegacy .userinfo .userinfo_extra {     float:right!important;     width:70px;     margin-top:0; }
```is what directly affects that section
i sugest messing with styles using chrome's built in firebug imitation (firebug is better)
the new code should be in the last style tag under the head element
html-> head->style

---

### Post by vasa1 on 2013-03-04
> **pqwoerituytrueiwoq said:**
> i could but, i cant guarantee it will work without the code you are using already

I'm posting a link to a total of **three** style sheets, two in Stylish and this: ~/.config/google-chrome/Default/User Stylesheets/Custom.css. 

I must also mention that I use Privoxy and AdBlock to remove other matter (image blocking and element hiding) I don't need to see and to block scripts I don't need. Then, of course, there are the forum's CP settings re. avatars and signatures.

Anyway, if you can help that will be most welcome.

Link: [https://docs.google.com/document/d/128PdjEM5OsXXHh2qCc6WS8jcAYRPXklA9WeEKB53SoU/edit?usp=sharing](https://docs.google.com/document/d/128PdjEM5OsXXHh2qCc6WS8jcAYRPXklA9WeEKB53SoU/edit?usp=sharing)

---

