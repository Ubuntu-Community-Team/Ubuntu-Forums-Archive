---
title: "gedit automatic html closing tabs?"
date: 2009-09-22
forum: Desktop Environments
---

### Post by jaime256 on 2009-09-22
Hi. I'm making some html notes and was wondering if there's a way to have auto complete html closing tabs here? Here's an example:
<font color="#00FF00">6.1.1-4**</font>**<br><br>

I'm using the font tab quite a bit on each section and when I type </ under say screem it auto completes it for me. Unfortunately that program tends to act weird, meaning sometimes it lags for no reason so I don't mind using the regular text editor, but I don't wan to have to type this whole thing each time which takes longer or any closing tab so I can save a bit of time. I installed bluefish and Kompozer, but they don't auto complete either or if anyone can tell me how to turn this feature on would be appreciated since it would save me time. I just need something simple, but that doesn't close on me like Kompozer does or lag like screem. I hope the simple built in gedit can do this. I'm also using BOLD but don't know if this can also be automated so I don't have to type it each time. Thanks.

---

### Post by Rab22 on 2009-09-22
> **jaime256 said:**
> Hi. I'm making some html notes and was wondering if there's a way to have auto complete html closing tabs here? Here's an example:
<font color="#00FF00">6.1.1-4**</font>**<br><br>

I'm using the font tab quite a bit on each section and when I type </ under say screem it auto completes it for me. Unfortunately that program tends to act weird, meaning sometimes it lags for no reason so I don't mind using the regular text editor, but I don't wan to have to type this whole thing each time which takes longer or any closing tab so I can save a bit of time. I installed bluefish and Kompozer, but they don't auto complete either or if anyone can tell me how to turn this feature on would be appreciated since it would save me time. I just need something simple, but that doesn't close on me like Kompozer does or lag like screem. I hope the simple built in gedit can do this. Thanks.

Not sure if this will work for you or not, but you can take a look at the Plugin called "Snippets". I use it quite a bit and it may work for you.

Also, if you look at the bottom of that screen shot you'll see a plugin called "Tags". Not sure what that does, you may want to take a peek at it too.

---

### Post by jaime256 on 2009-09-22
Thanks, I did add that tags but still didn't do it. I have no idea what it does. What does the snippet do for you?

---

### Post by Rab22 on 2009-09-22
> **jaime256 said:**
> Thanks, I did add that tags but still didn't do it. I have no idea what it does. What does the snippet do for you?

It auto generates code with the use of 'tab completion'.  For example, turn it on and type "meta" and hit tab. It should auto generate the META tag for you.

---

### Post by jaime256 on 2009-09-22
I see, maybe it's the way I'm not using it. I'll try that and see how that works. I'm still using screem since I got some shortcuts on the toolbar to bold and things like that too, but that one still gets annoying to use at times.

---

### Post by jaime256 on 2009-10-03
Well I tried that meta and tab, that works for that but not for what I want. Either that or I have to know what it's called in order to have it finished my tab, but it's just a closing tab and that didn't work. I like gedit but I wish there was a way for me to do this. If anyone finds a way to do it please let me know, but if there's something close with this bit of extra stuff in the editor please let me know. Thanks.

---

### Post by rystraum on 2009-10-05
Under Tools > Manage Snippets, you can see all the available tags currently.
The tab trigger is what you type in before pressing the tab button to invoke the snippet.
Example:
I have:
```
<font> $0 </font>
```
Tab trigger: font

If I type font, and then press tab, it should substitute ```
<font> </font>
``` where the word was. [You can read further about it here]("http://live.gnome.org/Gedit/Plugins/Snippets"). I recently started using it for Ruby on Rails dev and I'm building up my list as I go, so I admittedly don't know so much about the plugin.

Also, I'd like to point out that the ```
<font>
``` tag is deprecated and stylesheets should be used in lieu of these tags. Just wanted to point it out. :)

---

### Post by jaime256 on 2009-10-16
Thank you for that information. I didn't know that was there. I learned basic html a long time ago and haven't used any css and so far it just keeps my pages simple that's why I keep using it, but I guess it shouldn't matter if it's under the css so I tried it, but can't seem to make it work. As you see on the attached picture I can't type anything on the shorcut window. How do you activate these? Do you choose it and close it? I know it seems trivial but I also type font and tab, but it doesn't work on my end.

I thought if I add my own html font snippet, but I can't add anything there either.

---

### Post by rystraum on 2009-10-16
Hmm. It's also important to note that snippets listed under HTML only activate when you are editing a .html file, CSS when you are editing .css files and so on. It may be that you have just created the file (thus it's still unsaved, and untyped) that's why the snippets are not activating. You can try saving the file first as the type that you want it to be. Snippets under Global, as the name implies, is always present, no matter what type of document you are editing.

Also, sometimes when I'm adding new snippets, they don't work at first. In such cases, I restart gedit and it works most of the time.

For the shortcut window, you just press the shortcut combination that you want. You need not type it. :)
Beware though, because the snippet does not check whether or not that shortcut combination is already assigned to a command. For instance, you can map a snippet to Ctrl+W, but that does not override the close function that is already assigned to Ctrl+W. :)

---

### Post by jaime256 on 2009-10-18
Thanks! I went ahead and tested adding a snippet and then I tried it. Didn't work. I then saved the txt file, renamed it to test.html and it worked. 

I figured I go back and test it with a regular txt file, and it also works.

This was after I added the snippet into the global and figured out how to actually add one. I typed the name font in the tab trigger or else it won't work of course. I then tabbed to the shortcut key and pressed the tab key, but nothing happens so I'm not sure if it works and you're not supposed to see anything, but after doing this and closing the window. I went back to the txt file and it worked just like you had described before. Then again the word tab is in there before trigger so I may just have been looking into it a bit more than the obvious. :) This will be extremely helpful now that I can just add the ones I used which are not many since I mainly use text on the page. Of course putting them in the correct place will keep things organized, like you said under html, css, etc.

For anyone else trying to figure this one out, you can also just mouse over the Activation names and it will tell you what you need to do. It took me a few seconds to figure it out, but sometimes things just don't make any sense. Now does anyone know where the settings for the gedit are so that if and when I do a clean install I can just bring all this back without having to write them in again?

I do hope they can add that where the snippets does check to see if a short cut has been assigned. That would be more useful too.

> **rystraum said:**
> Hmm. It's also important to note that snippets listed under HTML only activate when you are editing a .html file, CSS when you are editing .css files and so on. It may be that you have just created the file (thus it's still unsaved, and untyped) that's why the snippets are not activating. You can try saving the file first as the type that you want it to be. Snippets under Global, as the name implies, is always present, no matter what type of document you are editing.

Also, sometimes when I'm adding new snippets, they don't work at first. In such cases, I restart gedit and it works most of the time.

For the shortcut window, you just press the shortcut combination that you want. You need not type it. :)
Beware though, because the snippet does not check whether or not that shortcut combination is already assigned to a command. For instance, you can map a snippet to Ctrl+W, but that does not override the close function that is already assigned to Ctrl+W. :)

---

