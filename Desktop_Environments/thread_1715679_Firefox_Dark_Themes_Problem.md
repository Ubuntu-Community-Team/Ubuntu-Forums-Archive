---
title: "Firefox Dark Themes Problem"
date: 2011-03-27
forum: Desktop Environments
---

### Post by fullmoonguru on 2011-03-27
This is not the usual menu or text box problem.  My default system font color is grey.  I think what is happening is that some web pages don't define a font color so I end up with gray on white.  The menu in FF allows you to choose font & background colors, but then it overrides the web pages.  What I want is to change just the default font color (to black), within FF, so that black will be the color if the web page specifies the default color.  I looked in about:config but was not successful.

---

### Post by Krytarik on 2011-03-27
This is the "userContent.css" included by the Elegant Gnome theme, copy it into the "chrome" directory of your Firefox profile, "~/.mozilla/firefox/*.default", or merge it with your own. Then try to filter out the specifications you don't need/want.
```
input {
border: 2px inset white;
background-color: white;
color: black;
-moz-appearance: none !important;
}

textarea {
border: 2px inset white;
background-color: white;
color: black;
-moz-appearance: none !important;
}

select {
border: 2px inset white;
background-color: white;
color: black;
-moz-appearance: none !important;
}

input[type="radio"],
input[type="checkbox"] {
border: 2px inset white ! important;
background-color: white ! important;
color: ThreeDFace ! important;
-moz-appearance: none !important;
}

*|*::-moz-radio {
background-color: white;
-moz-appearance: none !important;
}

button,
input[type="reset"],
input[type="button"],
input[type="submit"] {
border: 2px outset white;
background-color: #eeeeee;
color: black;
-moz-appearance: none !important;
}

body {
background-color: white;
color: black;
display: block;
margin: 8px;
-moz-appearance: none !important;
}
```
Greetings.

---

### Post by Dngrsone on 2011-03-31
Awesome!  Fixed a problem I've been putting up with for months:  some forums (including this one and facebook) I just couldn't read what I was typing.

---

### Post by jworks on 2011-10-05
Another problem solved :) Thanks!

---

### Post by fullmoonguru on 2011-10-05
Yes, I forgot to answer & thank you.  Worked for me too!

---

### Post by Bill Gates Foundation on 2012-01-02
CAN some body explain the directions......more simply about how to merge.......Mr. Gates is tired of looking a white on off white  web pages.......craigslist is impossible to see:popcorn:

---

### Post by Bill Gates Foundation on 2012-01-02
what doi i need to change?

---

### Post by Dngrsone on 2012-05-02
> **Bill Gates Foundation said:**
> CAN some body explain the directions......more simply about how to merge.......Mr. Gates is tired of looking a white on off white  web pages.......craigslist is impossible to see:popcorn:

Copy the contents of the code box and paste it into a text editor such as gedit.  Save As userContent.css and then move that file into the Chrome folder in your Firefox profile.  You may have to create the Chrome folder.

Restart Firefox and it should be all happy.

---

