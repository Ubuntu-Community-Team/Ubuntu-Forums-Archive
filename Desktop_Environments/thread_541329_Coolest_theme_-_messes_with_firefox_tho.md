---
title: "Coolest theme - messes with firefox tho"
date: 2007-09-02
forum: Desktop Environments
---

### Post by wconstantine on 2007-09-02
Ok. I've got a huge problem. Just ran into the nicest theme available. Image 1. It looks so damn good. But when I fire up firefox I get problems. The theme makes it look like ****. See image 2. Anyone that knows how I should solve this?

Image 1: [http://pici.se/pictures/EiCgoWUdW.png](http://pici.se/pictures/EiCgoWUdW.png)
Image 2: [http://pici.se/pictures/lNEQLPyoB.png](http://pici.se/pictures/lNEQLPyoB.png)

Please, I'm in flames over this theme!

---

### Post by banewman on 2007-09-02
Try this for firefox themes - [https://addons.mozilla.org/en-US/firefox/browse/type:2/cat:61](https://addons.mozilla.org/en-US/firefox/browse/type:2/cat:61) - fourth down looks right. enjoy :)

---

### Post by yabbadabbadont on 2007-09-02
It is a known issue with Firefox, that dark themes play havoc with it.  The only solutions that I have seen have to do with creating a custom userChrome.css (or something like that) to force the colors to be reasonable.

Edit: Too slow.  :D

---

### Post by merlinus on 2007-09-02
> **wconstantine said:**
> Ok. I've got a huge problem. Just ran into the nicest theme available. Image 1. It looks so damn good. But when I fire up firefox I get problems. The theme makes it look like ****. See image 2. Anyone that knows how I should solve this?

Image 1: [http://pici.se/pictures/EiCgoWUdW.png](http://pici.se/pictures/EiCgoWUdW.png)
Image 2: [http://pici.se/pictures/lNEQLPyoB.png](http://pici.se/pictures/lNEQLPyoB.png)

Please, I'm in flames over this theme!

What is the theme and where can I get it?

yabbadabbadont is correct.  I use dark themes, and have created a userChrome.css file for firefox that works great for most everything, including this forum.

-merlin

---

### Post by Lord Illidan on 2007-09-02
Yeah, what is this theme, please?

---

### Post by z0phi3l on 2007-09-02
> **merlinus said:**
> What is the theme and where can I get it?

yabbadabbadont is correct.  I use dark themes, and have created a userChrome.css file for firefox that works great for most everything, including this forum.

-merlin

I'd like to know the theme and what you did to your userChrome to fix the same problem

---

### Post by merlinus on 2007-09-02
Here are some of the dark themes that I use.  They should all be available at gnome-look.org.

46165-Clearlooks_blackblue.tar.gz
46238-MurrinaBlackBlue.tar.gz
54166-Murrina-Neutronium_DeepBlack.tar.gz
63549-GTK-BlueGlow.tar.gz

And here is my userContent.css:

> 
/*
 * Edit this file and copy it as userContent.css into your
 * profile-directory/chrome/
 */

/*
 * This file can be used to apply a style to all web pages you view
 * Rules without !important are overruled by author rules if the
 * author sets any.  Rules with !important overrule author rules.
 */

/*
 * example: turn off "blink" element blinking
 *
 * blink { text-decoration: none ! important; }
 *
 */

/*
 * example: give all tables a 2px border
 *
 * table { border: 2px solid; }
 */

/*
 * example: turn off "marquee" element
 *
 * marquee { -moz-binding: none; }
 *
 */
 
/* 
 * For more examples see [http://www.mozilla.org/unix/customizing.html](http://www.mozilla.org/unix/customizing.html)
 */
 
textarea, input {
  color: #000 !important;
  background-color: #fff !important;
   }
 
   /* Single line text fields */
input {
  /* Set font size and family of text fields */
  font-family: clean !important;
  font-size: 13px !important;

  /* Set background color to something a little prettier
  background-color: rgb(200, 255, 220) !important; */

  /* Add some key bindings.
   * For an explanation of how to do this,
   * see below under "Custom key bindings".
   
  -moz-binding: url("resource:///res/builtin/myHTMLBindings.xml#myInputFields") !important;
}*/


/* The  dropdown address and autocomplete windows are grey.
 * To make them match better with the URL field and look more like 4.x:
 */

/*  URL dropdown box  
#ubhist-popup
  {
    background            : white !important;
    border                : 1px solid black !important;
    padding               : 0px !important;            
  }
*  autocomplete text field  */
.textfield-popup
  {
    background            : white !important;
    border                : 1px solid black !important;
  }*/

#ubhist-popup > .popup-internal-box, .textfield-popup > .popup-internal-box
  {
    border-left           : 1px solid white !important;
    border-top            : 1px solid white !important;
    border-right          : 1px solid white !important;
    border-bottom         : 1px solid white !important;
  }
  textarea {
  min-width: 50ex !important;
  min-height: 12em !important;
  color: #000 !important;
  background-color: #fff !important
}
slider {
   height: 20px !important;
   color: #fff !important;
   background-color: #000 !important
}
slider[align="vertical"] {
   width: 20px !important;
}
select, option {
 color: #000 !important;
  background-color: #fff !important
}
-merlin

---

### Post by PmDematagoda on 2007-09-02
Really sorry for asking this but where is the userContent.css file located?:confused:

---

### Post by merlinus on 2007-09-02
Open Nautilus, and make sure Show Hidden Files is activated.

Then look in .mozilla/firefox/xxxxxxxx.default/chrome.

(xxxxxxx refers to numbers and letters that are different for everyone)

You can copy-and-paste mine into that folder.  Be sure to name it userContent.css

There is a sample one there already, and you can either edit it, or use mine as a starting point.

-merlin

---

### Post by PmDematagoda on 2007-09-02
I did that and when I tried with the Ubuntu Ultimate theme Firefox still took the black colour of the theme. Here's my edited userContent.css:

```
/*
* Edit this file and copy it as userContent.css into your
* profile-directory/chrome/
*/

/*
* This file can be used to apply a style to all web pages you view
* Rules without !important are overruled by author rules if the
* author sets any. Rules with !important overrule author rules.
*/

/*
* example: turn off "blink" element blinking
*
* blink { text-decoration: none ! important; }
*
*/

/*
* example: give all tables a 2px border
*
* table { border: 2px solid; }
*/

/*
* example: turn off "marquee" element
*
* marquee { -moz-binding: none; }
*
*/

/*
* For more examples see http://www.mozilla.org/unix/customizing.html
*/

textarea, input {
color: #000 !important;
background-color: #fff !important;
}

/* Single line text fields */
input {
/* Set font size and family of text fields */
font-family: clean !important;
font-size: 13px !important;

/* Set background color to something a little prettier
background-color: rgb(200, 255, 220) !important; */

/* Add some key bindings.
* For an explanation of how to do this,
* see below under "Custom key bindings".

-moz-binding: url("resource:///res/builtin/myHTMLBindings.xml#my InputFields") !important;
}*/


/* The dropdown address and autocomplete windows are grey.
* To make them match better with the URL field and look more like 4.x:
*/

/* URL dropdown box
#ubhist-popup
{
background : white !important;
border : 1px solid black !important;
padding : 0px !important;
}
* autocomplete text field */
.textfield-popup
{
background : white !important;
border : 1px solid black !important;
}*/ 
```

---

### Post by merlinus on 2007-09-02
Can you be more exact in your description?

For me, this forum's message posting box is white and the text I type is black.

-merlin

---

### Post by PmDematagoda on 2007-09-02
I may be terribly wrong, the firefox menu bars take the colour of the theme, though I didn't try looking at the colour of the text which is more important:-\", my bad. Sorry Merlin.

---

### Post by PmDematagoda on 2007-09-02
Well I don't know what I'm doing but when I visit a site like Gmail while using something like the Ubuntu Ultimate theme the letters are white on white which means I need to highlight them to see them, do you have suggestion for this Merlin?

---

### Post by merlinus on 2007-09-02
I just loaded gmail.com, and it is black text on a white background.

Check your firefox edit/preferences/content/colors and make sure allow pages to use their own colors is checked.

-merlin

---

### Post by PmDematagoda on 2007-09-02
Yup it works now, thanks for all your help and for bearing with me merlin.:grin:

---

### Post by merlinus on 2007-09-02
Glad I could help, and that things are working.

-merlin

---

### Post by wconstantine on 2007-09-03
Thanks for the feedback folks, gonna try it when I come home. =)

Edit:

The gtk theme is Mire by Thrynk. Emerald theme is Scaled Black Mod.

---

