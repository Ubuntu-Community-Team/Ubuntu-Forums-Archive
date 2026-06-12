---
title: "Browser form controls"
date: 2005-10-30
forum: Desktop Environments
---

### Post by pooky on 2005-10-30
Is there any way to make gekko/firefox use the current gnome theme's controls (textbox, dropdown, scrollbar etc)? I dont know where the one's being used come from, but they're ugly! I'm on ubuntu BB.
In Windows, the controls used in the browser seem to be the ones from the OS.
Not sure about OSX but the aqua controls in the safari at least look nice.
 I'm pretty new to linux so if someone's kind enough to explain then bear that in mind ;)
thanks

---

### Post by poptones on 2005-10-30
I just made a very simple userChrome file. Copy the text below, paste it into the text editor and save it to a file called "userChrome.css" (note the capitalization) in your mozilla folder under the path:

.mozilla/firefox/**default.zig**/chrome/userchrome.css

In your firefox folder there may be more than one "zig" (profile) folder. Make sure to put the text file in the one you are using. An easy way to check is to click on your bookmarks - the default ones are only about 5kb but yours is likely larger :)

This will give you very plain forms, but at least they look nicer than the defaults. Of course, now that you know how it works you can mod this one to suit yourself...

```


input, textarea, select, checkbox, radio {
	margin-bottom: 2px;
	border: 1px solid #393939;
	background-color: #fff;
	color: #393939;
}

option {
	margin-bottom: 2px;
	border: none;
	background-color: #F2F6FC; }

input:active, input:focus, textarea:active, textarea:focus {
	border: 1px solid #ed7979;
	background: #fff;
}

```

---

