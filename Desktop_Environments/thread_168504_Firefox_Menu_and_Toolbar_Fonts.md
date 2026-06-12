---
title: "Firefox Menu and Toolbar Fonts"
date: 2006-04-30
forum: Desktop Environments
---

### Post by charlie. on 2006-04-30
I have installed kubuntu-dektop on a Dapper Drake machine. Everything is working perfectly and it responds much faster than the Ubuntu Gnome desktop on the same machine. (a LOT faster!) Firefox is worrying, however...

The fonts that are used in the Firefox user interface are HUGE - they must be about 12pt fonts.

While the actual content displayed in the browser window is normally sized, because most sites override defaults with their style sheets, the captions of buttons and text on the menu items is incredibly big. Does anyone know how to change this? Changing the font sized under "System Settings" -> "Appearance" does not affect Firefox.

---

### Post by charlie. on 2006-04-30
I downloaded the latest binaries from mozilla's site and ran them. They work perfectly and all the fonts are much more reasonable. Additionally, performance has been improved dramatically. Changing the text size, a feature I use very frequently when reading long articles, is now incredibly smooth.

---

### Post by pcormack on 2006-05-01
I'm new to Kubuntu also.
Firefox, GAIM etc are GTK apps, if you open a terminal and type kcontrol it will open the control center for KDE.

Appearence & Themes >> GTK styles and fonts

and alter the fonts from there. You'll need to restart firefox/ other GTK apps after each change in order to view the differences. Thats how I got the firefox menu and toolbar fonts down as they where absolutely massive!

---

### Post by charlie. on 2006-05-01
I gathered that GTK was involved. Thanks pcormack. (I still think that KDE does a better job of displaying GTK apps than Gnome does of Qt.)

Now that I am using the firefox binaries from Mozilla's website, the UI fonts are correctly sized. Apparently, the whole UI has been scaled down. This means that, while the UI is correctly sized, the content is now minute! I have tried changing the default font size in firefox but that failed to correct the problem.

---

### Post by hermesrules on 2006-05-02
[QUOTE=pcormack]I'm new to Kubuntu also.
Firefox, GAIM etc are GTK apps, if you open a terminal and type kcontrol it will open the control center for KDE.

Appearence & Themes >> GTK styles and fonts

and alter the fonts from there. You'll need to restart firefox/ other GTK apps after each change in order to view the differences. Thats how I got the firefox menu and toolbar fonts down as they where absolutely massive![/QUOTE]

For whatever reason, this no longer really works for me the way it is supposed to. Now when I go into the applet, and select a custom font (or the defaults), it always goes back to my previous selection. Thus, I can't change the font for GTK applications. I find this bizzare, to say the least. Does anyone have an idea what might I need to change? Icons seem to be working, it is only the font that refuses to change...

---

### Post by BobBlum on 2006-07-15
I just went through the same problems with the KDE interface to Ubuntu.  All GTK (GNOME) apps (e.g., synaptic) had tiny menu fonts if Firefox had correctly sized fonts.  To make the fonts in the GTK applications assume the correct size, I had to install gtk2-engines-gtk-qt.  But this will not be enough.  Read on:

After installing gtk2-engines-gtk-qt, access it by clicking the K-Start button, and then selecting Sytem Settings, Appearance, and GTK styles and fonts.

Under GTK Styles, click the radio button labelled "Use another style"
In the drop-down menu, an excellent choice is "Crux," but "Human" will also work.

Under GTK Fonts, click the radio button labelled "Use another font"
In the drop-down menu, an excellent choice is "DejaVu Sans (size 13).

Click "Apply."

Now bring up a GTK (GNOME) application such as synaptic of Thunderbird.  You will see that the font sizes in the application menus are acceptable.

Now bring up Firefox.  You will find that the fonts in the application menus are enormous.  We have to correct that by installing a userChrome.css script in the .mozilla direcory.

Here is how to create the userChrome.css file:

Using Konqueror, go to your home directory.
On the top-line menu, click View and put a check mark next to "Show Hidden Files"

Now, locate the hidden subdirectory named .mozilla.  Open it.
Then open the Firefox subdirectory.  In it, you will see a directory with a randomly generated name followed by .default.  Click on that subdirectory to open it.

You will now see a subdirectory labelled "Chrome."  Click on it to open it.

Create a text file named userChrome.css

In that text file, copy the following code (there are many variations but the following code has worked well for me):

-------------------------------------------------------------
/* You can set the font globally. */
* {
   font-family: 'dejavu sans',verdana,sans-serif !important;
   font-size: 9pt !important;     /* uncomment this entry if you want a fixed size. */
}


  /* Add some key bindings.
   * For an explanation of how to do this,
   * see below under "Custom key bindings".
   */
  -moz-binding: url("resource:///res/builtin/myHTMLBindings.xml#myInputFields") !important;
}


/* Fix text input boxes. */
input[type],
input[name] {
   font-size: 10pt !important;
}

/* Multi-line textareas */
textarea {
  background-color: rgb(200, 255, 220) !important;
}

/* The  dropdown address and autocomplete windows are grey.
 * To make them match better with the URL field and look more like 4.x:
 */

/*  URL dropdown box  */
*#ubhist-popup
  {
    background            : white !important;
    border                : 1px solid black !important;
    padding               : 0px !important;            
  }

/*  autocomplete text field  
.textfield-popup
  {
    background            : white !important;
    border                : 1px solid black !important;
  } */

#ubhist-popup > .popup-internal-box, .textfield-popup > .popup-internal-box
  {
    border-left           : 1px solid white !important;
    border-top            : 1px solid white !important;
    border-right          : 1px solid white !important;
    border-bottom         : 1px solid white !important;
  }

/* 3. Add a border (line of 1px) to the tooltips. */
.tooltip-label
/*   {
     border                : 1px solid !important;
   } */


/* Specify the font used for the subject in the message pane
 * (it was bold, fixed-width and too wide).
 */
.subjectvalue {
  font-family; dejavu-sans !important;
  font-weight: normal !important;
}

/* Make the thread and folder panes readable. */
treechildren {
  	font-family: 'dejavu sans',verdana,sans-serif !important;
	font-size: 12px !important;
}

/* Change the background colour of the messages (top right hand
 * pane in 3-pane view) of Mail/News from gray to white.
 */
outliner {
     background-color : white !important;
}

/* Set font size and family for dialogs
 * and other miscellaneous text
 */
window {
  font-size: 12px !important;
  font-family: sans !important;
}


/* tab group bookmarks  */
menuitem.bookmark-group {
   color: brown !important;
   font-style: normal !important;
   font-size: 12px !important;
} 

/* Show tab loading indicator while the tab is loading */

.tabbrowser-tabs *|tab[busy] .tab-icon {
  display:-moz-box;
}

/* Shrink tab titles by 10% 
.tabbrowser-tabs .tab-text {
  font-size: 40%;
} */

------------------------------------------------------

That's it.  That should solve the problem of the Firefox menu fonts under KDE.
In coming up with the code for the userChrome.css file, I relied heavily on the following Web sites:

[http://berkano.net/bits/](http://berkano.net/bits/)
[http://www.tom-cat.com/](http://www.tom-cat.com/)
[http://www.mozilla.org/unix/customizing.html#usercss](http://www.mozilla.org/unix/customizing.html#usercss)

The procedures desicribed above have completely solved the KDE-Firefox-GTK font problems for me.  I hope they may be of help to you.  I really hope that there is some simpler method for doing this that I was not aware of.  I also hope that developers of KDE distributions will begin to include default configurations that make these efforts unnecessary in the future.  Although I use Kubuntu and Ubuntu, I have experimented with the Fedora distribution and found that the problems with the Firefox fonts do not exist in that distribution, although I have not been able to ascertain how they have dealt with them in Fedora.

---

### Post by pete205 on 2007-06-27
Thanks BobBlum, this fix works for the same problem in Xfce too

---

