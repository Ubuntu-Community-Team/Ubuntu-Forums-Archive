---
title: "lightdm-webkit greeter input type=&quot;text&quot; autocompletion support"
date: 2014-12-31
forum: Desktop Environments
---

### Post by Josep_Mulet on 2014-12-31
I want to create a custom lightdm greeter using webkit.

As an starting point I have downloaded this theme
[CENTER][https://github.com/omgmog/lightdm-webkit-google](https://github.com/omgmog/lightdm-webkit-google)[/CENTER]
which almost meets my requirements.

I have tried to change the select html component with an input text. So far, so good.
I wanted to go one step further and provide the input text component with autocompletion.

I did this using standard html 

<datalist id="list1">
    <option value="user1">user1</option>
    <option value="user2">user2</option>
</datalist>

<input id="user" type="text" list="list1"/>

(Well, actually I filled the list1 with javascript)

I tested the greeter in a web browser (firefox and chrome) and everything was OK. 
I restarted lightdm and I found that no autocompletion was shown.
Then I checked that If I replaced the <input> element with a <select> everything works well again.

Anyone knows which is the problem? Is autocompletion supported in lightdm webkit?

---

