---
title: "Post your userChrome.css"
date: 2007-07-17
forum: Desktop Environments
---

### Post by AndrewGene on 2007-07-17
I have been messing around a lot lately with the userChrome.css file for firefox and have found it quite interesting.  I am just wondering what everyone else's looks like to see if i can glean some more ideas from them...
here is my userChrome.css...

/*
 * Eliminate the throbber and its annoying movement:
 */
 #throbber-box {
   display: none !important;
 }
 
#navigator-toolbox .menubar-text {
	color: #ffffff !important;
}
/* background image for all toolbars */ 
toolbox,
#toolbar-menubar,
 #nav-bar,
  #PersonalToolbar,
   #FindToolbar,
    tabbox,
     sidebarheader,
      #sidebar-box
{
        -moz-appearance: none !important;
         background-image: url('drops.png.png') !important;
          background-color: transparent !important;
          }
  /* change corners of tabs */
   tab {
    border: #FFFFFF 2px solid !important;
    border-bottom: 0px !important;
    -moz-border-radius-topleft: 4px !important;
    -moz-border-radius-topright: 4px !important;
    -moz-border-radius-bottomleft: 0px !important;
    -moz-border-radius-bottomright: 0px !important;
    -moz-border-corner-fit: scale !important;
    }
    /* change bookmark toolbar label font */
     #personal-bookmarks .toolbarbutton-text {
     font-size: 8pt !important;
     font-weight: bold !important;
     color: #ffffff 
      }
      /* change background of status toolbar */
//window statusbarpanel {
 // -moz-appearance: none !important;
 // background-image: url('drops.png.png') !important;
  //background-color: transparent !important;
//}
/* hide the Back button when there's nothing to go back to */
 #back-button[disabled="true"] {
  display: none !important; }
   /* hide the Forward button when there's nothing to go forward to */ 
   #forward-button[disabled="true"] { 
   display: none !important; }
    /* hide the Stop button when there's nothing to stop */
     #stop-button[disabled="true"] {
      display: none !important; }
      /* hide the dropdown arrows on forward and back buttons */
       #back-button .toolbarbutton-menubutton-dropmarker,
        #forward-button .toolbarbutton-menubutton-dropmarker {
         display: none !important; }

and a picture of my FF...

---

### Post by AndrewGene on 2007-07-17
anyone???

---

### Post by kerry_s on 2007-07-18
hmm, i like the transparent background, going to have to snag that. :)
I had auto hide for my tool bars but it got annoying.

```
/*
 * Edit this file and copy it as userChrome.css into your
 * profile-directory/chrome/
 */

/*
 * This file can be used to customize the look of Mozilla's user interface
 * You should consider using !important on rules which you want to
 * override default settings.
 */

/*
 * Do not remove the @namespace line -- it's required for correct functioning
 */
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul"); /* set default namespace to XUL */


/*
 * Some possible accessibility enhancements:
 */
/*
 * Make all the default font sizes 20 pt:
 *
 * * {
 *   font-size: 20pt !important
 * }
 */
/*
 * Make menu items in particular 15 pt instead of the default size:
 *
 * menupopup > * {
 *   font-size: 15pt !important
 * }
 */
/*
 * Give the Location (URL) Bar a fixed-width font
 *
 * #urlbar {
 *    font-family: monospace !important;
 * }
 */

/*
 * Eliminate the throbber and its annoying movement:
 *
 * #throbber-box {
 *   display: none !important;
 * }
 */

/*
 * For more examples see http://www.mozilla.org/unix/customizing.html
 */


/*tranparent tabs*/
.tabbrowser-tabs {
  background-color: transparent !important;
  background-image: none !important;
}

.tabs-bottom {
  height: 0 !important;
}

.tabbrowser-tab {
  padding: 0 !important;
  margin: 2px !important;
}

.tabbrowser-tab:not([selected="false"]) {
  -moz-appearance: button !important;
}

.tabbrowser-tab:not([selected="true"]) {
  -moz-appearance: button !important;
}

.tabbrowser-tab[selected="false"] {
  -moz-appearance: textfield !important;
  margin-left: 0 !important;
  padding-left: 1px !important;
}

.tabbrowser-tab[selected="true"] {
  -moz-appearance: textfield !important;
  margin-left: 0 !important;
  padding-left: 1px !important;
}

.tab-image-left, .tab-image-middle, .tab-image-right, .tab-close-button {
  background-image: none !important;
  background-color: transparent !important;
}

.tab-image-left {
  width: 4px !important;
}

.tab-image-middle {
  padding-top: 0 !important;
}

.tabbrowser-tab[selected="false"] > .tab-image-left,
.tabbrowser-tab[selected="false"] > .tab-image-middle,
.tabbrowser-tab[selected="false"] > .tab-image-right,
.tabbrowser-tab[selected="false"] > .tab-close-button {
  background-color: transparent !important;
}

.tabbrowser-tab[selected="true"] > .tab-image-left,
.tabbrowser-tab[selected="true"] > .tab-image-middle,
.tabbrowser-tab[selected="true"] > .tab-image-right,
.tabbrowser-tab[selected="true"] > .tab-close-button {
  background-color: transparent !important;
}

/* Disable "List all Tabs" Button */
.tabs-alltabs-button {
display: none !important;
}

/* Disable Container box for "List all Tabs" Button */
.tabs-alltabs-box {
display: none !important;
}

```

---

### Post by kerry_s on 2007-07-18
Can you wrap your code in code markers(# in the top menu) i think they got screwy.
:(

---

### Post by AndrewGene on 2007-07-18
> **kerry_s said:**
> Can you wrap your code in code markers(# in the top menu) i think they got screwy.
:(

What do you mean??? So you can copy paste it better or something???

I would be interested to see your tabs please...also, how did you move the address bar to the right of the top toolbar?

---

### Post by kerry_s on 2007-07-18
> **AndrewGene said:**
> What do you mean??? So you can copy paste it better or something???

I would be interested to see your tabs please...also, how did you move the address bar to the right of the top toolbar?

Yeap, they weren't lined up right :) ,but that's okay i got it, i just need to find a background image. The screen shot shows 2 tabs open, there just not very noticable. don't mind the yellow, i just grabbed a section off my notepad for now.

---

### Post by kerry_s on 2007-07-18
Sorry, missed 1 question, i was tired. I use tiny menu and then just put everything beside it.
[https://addons.mozilla.org/en-US/firefox/addon/1455](https://addons.mozilla.org/en-US/firefox/addon/1455)

You have any good links for the tool bar background? I just grabbed a screen shot section of my notepad to use for now.

---

### Post by strabes on 2007-07-18
Really the only thing I did was move vertical scrollbars 2px to the right so that when firefox is maximized I can just move my mouse all the way to the right of the screen & grab to scroll instead of having it grab the edge of the window. (for resizing)

scrollbar[orient="vertical"] scrollbarbutton,
scrollbar[orient="vertical"] slider{
margin-right: -1px !important;
margin-left: -1px !important;
}

---

### Post by AndrewGene on 2007-07-18
> **kerry_s said:**
> Sorry, missed 1 question, i was tired. I use tiny menu and then just put everything beside it.
[https://addons.mozilla.org/en-US/firefox/addon/1455](https://addons.mozilla.org/en-US/firefox/addon/1455)

You have any good links for the tool bar background? I just grabbed a screen shot section of my notepad to use for now.

You can use any size image of any format that firefox can handle...I used this one though...

---

### Post by kerry_s on 2007-07-18
Ahh, i see your just using a standard 800x600 background. I've just been grabbing a bar size section.lol. I haven't found anything that agrees with me yet, for now i went with the stock gray(no image).

---

### Post by AndrewGene on 2007-07-18
You might be interested in this site.

[http://www.linnhe2.free-online.co.uk/firefox/chrome.html](http://www.linnhe2.free-online.co.uk/firefox/chrome.html)

---

### Post by kerry_s on 2007-07-18
Thanks, i'll check that out now. laters.

---

