---
title: "Firefox &quot;bookmark toolbar&quot; text smaller"
date: 2007-12-20
forum: Desktop Environments
---

### Post by oddworld on 2007-12-20
In firefox, I would like to the text smaller on the bookmark toolbar, shown here:

[IMG]http://img139.imageshack.us/img139/6738/screenshotyw9.png[/IMG]

I want to fit all of my bookmarks, but 6 of them do not fit. They all fit in xp, but I guess with the default text size a few of them are not fitting in in ubuntu.
Any ideas?

Thanks!

---

### Post by Adam590 on 2007-12-22
Specifically shrinking the text size, no, but there are several ways to use the bookmark toolbar more efficiently. You can actually have thousands of bookmarks available there in a neat, orderly fashion.

1. Remove titles: many bookmarks will have identifying favicons associated with them (often not activated until clicking the bookmark once). If you can easily recognize the favicon, then you don't need the bookmark's title, so right-click the bookmark, select "Properties", and delete the name.

2. Organize with folders: go to Bookmarks -> Organize Bookmarks and double click "Bookmarks Toolbar Folder" in the left pane. Then right-click in the right pane, select "New Folder", name the folder, and drag some of your bookmarks into it. This will create handy drop-down folders on your bookmarks toolbar. You can put folders within these folders, too.

3. If you really want to get nuts with it, you can create several different folders on the bookmarks toolbar, add as many bookmarks to them as you want, assign icons to the folders with userchrome tweaks, then cram those folder icons together. A howto for the folder icons tweak can be found [_here (see post 14)_]("http://firefox.group.stumbleupon.com/forum/55085/"). If you just want to change (reduce) the spacing between bookmark toolbar items, copy/paste the following code into your userChrome.css* file (instructions for modifying userChrome are in the above link):

[COLOR="Blue"]/* change space around bookmark toolbar icons */
#personal-bookmarks toolbarbutton {
margin: 0px -5px 0px -5px !important;
padding: 0px -5px 0px -5px !important;
}[/COLOR]

(adjust the margin and padding figures to suit your needs, noting that they are ordered **top, right, bottom, left**)



* the instructions in that link are for M$ users, but the only difference in Linux is the location of the userChrome folder:
/home/(username)/.mozilla/firefox/(Fx profile name)/chrome


Here's a picture showing the results of the tweaks. 
11 of those icons are folders. 
As you can see, they all take up very little space. :)

---

### Post by oddworld on 2007-12-22
That was extremely helpful, thank you very much!
There are a lot of things you mentioned that I didn't even know existed.
I think I am going to try using folders with just icons, 
Thanks again!

---

### Post by s0l3x on 2008-07-13
I know this is an old post, but I recently came upon this problem, and worked out a fix.

I use Firefox on Windows and Ubuntu, and sync my bookmarks between them using Foxmarks, but on Ubuntu, the buttons were huge and caused the toolbar to 'spill-over') 

Before:
[IMG]http://www.myego.ca/resources/before.png[/IMG]
After:
[IMG]http://www.myego.ca/resources/after.png[/IMG]

Here's the code I used in my userChrome file:

```

/* Menu Bar - Shrink and Fade Text */
#navigator-toolbox .menubar-text {
	font-size: 70% !important;
	color: #999 !important;
	}

/* URL Bar and Search Bar - Shrink and Fade Text*/
#urlbar, #searchbar{ 
	font-size: 85% !important; 
	color: #333 !important;
	}

/* Tabs - Shrink Font and Height*/
.tabbrowser-tabs {
	font-size: 80% !important;
	height: 20px !important; 
	}
.tabbrowser-strip { 
	height: 22px !important;
	}

/* Bookmarks Toolbar - Shrink Font and Size*/
#PersonalToolbar {
	font-size: 75% !important;
	padding: 0px !important;
	margin: 0px !important;
	max-height: 20px !important;
	}
	/* Seperators - Remove */
	#PersonalToolbar toolbarseparator {
		display: none !important;
		}
	/* Toolbar Buttons - Reduce Margins */
	#PersonalToolbar toolbarbutton {
		margin: 0 -5px 0 -1px !important;
		}
	/* Toolbar Icons - Shrink and Reduce Margins */
	#PersonalToolbar .toolbarbutton-icon {
		max-width: 12px !important;
		max-height: 12px !important;
		margin: 0px 2px 0px 0px !important;
		}

```

FYI, userChrome is located as follows:
```
 ~/.mozilla/firefox/<random>.default/chrome/userChrome.css
```

---

