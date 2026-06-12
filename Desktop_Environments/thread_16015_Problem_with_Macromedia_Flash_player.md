---
title: "Problem with Macromedia Flash player"
date: 2005-02-18
forum: Desktop Environments
---

### Post by Chrisb319 on 2005-02-18
[IMG]http://img235.exs.cx/img235/9678/flashtest2gs.jpg[/IMG] 

Inside the flash player there is no textm, when I try and get help by clicking on settings this white bar comes up with no text I can see the pictures but no text. I can't choose the songs within the player.

---

### Post by keyshawn on 2005-02-19
Can you give more information ? 
 - What website, (I'm presuming you're trying to view flash from a website) are you attempting to view this flash from ?
 
 [Providing more info, like the website name, the browser you're using, version of flash player, and other details would be much more helpful for those trying to help you ;) ]

---

### Post by kassetra on 2005-02-19
chrisb319:
  how are you trying to access [http://www.purevolume.com]("http://www.purevolume.com?") ? I went there directly by typing the location in my browser, and it works just fine for me -- but when I went there by clicking on links from some band sites, it didn't work so well.
  
  Here is what I'm using to access the site and listen to music:
  flashplugin-nonfree 7.0.25-5
  mozilla-firefox (Ubuntu package 1.0-2ubuntu4-warty99) from the backports repository
  
 So it might be that the version of flash that you have installed or the browser you're using isn't supporting the scripting features of the pureplayer.
  
 Can you tell me what browser/flash plugin you have? (You can go Help->About in your browser, and do a search in synaptic for flash)

---

### Post by Chrisb319 on 2005-02-20
[IMG]http://img16.exs.cx/img16/4882/lalal1rp.jpg[/IMG] 

that's what i'm talking about I have no text, I use Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7) Gecko/20041013 Firefox/0.9.3 (Ubuntu)  with flashplugin-nonfree 7.0.25-5 installed and I can play the muci fine but no text comes up.

---

### Post by kassetra on 2005-02-20
> Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7) Gecko/20041013 Firefox/0.9.3 (Ubuntu)   
 
 That looks like the culprit, possibly.
 
 Do you know how to add ubuntu backports to your repositories?
 
 You probably need to upgrade your version of firefox to the backports version in order to see the text.

---

### Post by Chrisb319 on 2005-02-20
[QUOTE=kassetra]That looks like the culprit, possibly.
 
 Do you know how to add ubuntu backports to your repositories?
 
 You probably need to upgrade your version of firefox to the backports version in order to see the text.[/QUOTE]

don't know  :sad:

---

### Post by WW on 2005-02-20
You might not need to upgrade firefox.  I'm running warty with firefox 0.9.3, and with the package flashplayer-mozilla installed from Marillat's repository.  I was able to see the song titles and play the songs at the purevolume site.

(I'm not sure, but it appears that flashplayer-mozilla and flashplugin-nonfree are really the same thing.  They both have a version number beginning with 7.0.25-*.  I'm using flashplayer-mozilla because at the time that I installed it, flashplugin-nonfree was not available.)

---

### Post by kassetra on 2005-02-20
[QUOTE=WW]They both have a version number beginning with 7.0.25-*. [/QUOTE]
 
 That little tiny version change is what makes the difference...  but it's possible that 0.93 firefox and the free flash player work together to show everything correctly and the 1.x firefox and the non-free flash player work together correctly.  Because I've got 1.x and non-free, and you have 0.93 & free... interesting.
 
 Chrisb319: 
 Here is how you add the backports repositories to synaptic:
 1. Open Synaptic.
 2. go to Settings->Repositories
 3. Click on the "New" button
 4. Leave the top box set to Binary (deb)
 5. Type this in for URI:
  ```
http://backports.ubuntuforums.org/backports/
``` 
 6. Type this in for Distribution:
  ```
warty-backports
``` 
 7. Type this in for Section(s):
  ```
main universe restricted multiverse 
``` 
 8. Click OK.
 9. Click on the Reload button in the main Synaptic toolbar.
 10. Search for mozilla-firefox
 11. Right click on the mozilla-firefox name and choose "Mark for Upgrade"
 12. Click Apply.

---

### Post by Chrisb319 on 2005-02-20
I did that but it still does not show any text

[q]Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.5) Gecko/20041209 Firefox/1.0 (Ubuntu) (Ubuntu package 1.0-2ubuntu4-warty99)[/q]

I have this now.

---

### Post by kassetra on 2005-02-20
Ok, I have a drastic measure for you to try then:  (it's only temporarily drastic, so no worries)
 
 1. exit firefox
 2. rename your .mozilla directory to 0.mozilla (if you don't know how to do this, I can help you)
 3. restart firefox
 4. type in [www.purevolume.com](www.purevolume.com) in the location bar and go there.
 5. do you see any text now?

---

### Post by Chrisb319 on 2005-02-20
[QUOTE=kassetra]Ok, I have a drastic measure for you to try then:  (it's only temporarily drastic, so no worries)
 
 1. exit firefox
 2. rename your .mozilla directory to 0.mozilla (if you don't know how to do this, I can help you)
 3. restart firefox
 4. type in [www.purevolume.com](www.purevolume.com) in the location bar and go there.
 5. do you see any text now?[/QUOTE]

How do I rename the directory?

---

### Post by kassetra on 2005-02-20
Ok:
 1. Open Nautilus (Computer->Home)
 2. go up to Edit->Preferences
 3. Checkmark (by clicking on it) Show hidden and backup files
 4. Click close
 5. Scroll down in your nautilus window until you see the .mozilla folder 
 6. Right click on it and then left click on Rename
 7. Rename it to 0.mozilla
 8. click your mouse somewhere outside of the nautilus window to make sure the new name sticks.

---

### Post by Chrisb319 on 2005-02-20
[QUOTE=kassetra]Ok:
 1. Open Nautilus (Computer->Home)
 2. go up to Edit->Preferences
 3. Checkmark (by clicking on it) Show hidden and backup files
 4. Click close
 5. Scroll down in your nautilus window until you see the .mozilla folder 
 6. Right click on it and then left click on Rename
 7. Rename it to 0.mozilla
 8. click your mouse somewhere outside of the nautilus window to make sure the new name sticks.[/QUOTE]

Still does not show any text and I lost my bookmarks.

---

### Post by kassetra on 2005-02-20
That's why I had you rename it instead of deleting it.
 
 Ok, so it looks like it might be your flash-player plugin.
 Go ahead and delete any .mozilla directories and rename the 0.mozilla to .mozilla
 
 Also, I would remove your flash plugin and then re-install it.

---

### Post by Chrisb319 on 2005-02-20
[QUOTE=kassetra]That's why I had you rename it instead of deleting it.
 
 Ok, so it looks like it might be your flash-player plugin.
 Go ahead and delete any .mozilla directories and rename the 0.mozilla to .mozilla
 
 Also, I would remove your flash plugin and then re-install it.[/QUOTE]
Still not working  :-|

---

### Post by kassetra on 2005-02-20
Ok... I know this is going to seem really, really silly... have you tried emptying your cache and reloading the page?

---

### Post by kassetra on 2005-02-20
WAIT!  Do you have msttcorefonts installed??

---

### Post by Chrisb319 on 2005-02-20
[QUOTE=kassetra]WAIT!  Do you have msttcorefonts installed??[/QUOTE]

I didn't now I do and now the text shows up :) Thanks :-)

---

### Post by kassetra on 2005-02-20
[QUOTE=Chrisb319]I didn't now I do and now the text shows up :) Thanks :-)[/QUOTE]
 
 Whew!  I was beginning to think I had lost my flash touch!  ;)

---

### Post by abock on 2005-04-05
I had this same problem under Hoary 5.04, Firefox 1.02. The problem, as one should expect when text doesn't show up, was that there were some fonts missing.

Installing "gsfonts-x11" did the trick for me.

$ sudo apt-get install gsfonts-x11

---

### Post by vtrac on 2005-04-14
[QUOTE=abock]I had this same problem under Hoary 5.04, Firefox 1.02. The problem, as one should expect when text doesn't show up, was that there were some fonts missing.

Installing "gsfonts-x11" did the trick for me.

$ sudo apt-get install gsfonts-x11[/QUOTE]
 Wow, I was missing msttcorefonts too.  Thanks.

---

### Post by 12quality on 2005-05-01
I had the same problem in Hoary and msttcorefonts solved the problem.  I didn't even need to restart Firefox; I just reloaded the page and the text was there. Thanks  :)

---

### Post by bpilgrim1979 on 2005-06-06
The font install worked for me too.  :)

But flash nonfree doesn't play sound for me in hoary.  :(

---

### Post by drumicube on 2005-06-13
Installing "gsfonts-x11" did the trick for me also !
Thanks a lot. :wink:

---

### Post by Sweezel on 2006-08-23
Can anyone get the Discount Tire "See wheels on your vehicle" to work with the Shockwave Flash plugin?

[http://www.discounttire.com/dtcs/interactive.dos](http://www.discounttire.com/dtcs/interactive.dos)

It just shows that I need the plugin even though other flash sites work fine.


Thanks!

---

### Post by Johan! on 2006-08-23
The site requires shockwave, not flash...
And there's no shockwave player for linux:sad:

---

### Post by rattlerviper on 2006-08-23
> **Sweezel said:**
> Can anyone get the Discount Tire "See wheels on your vehicle" to work with the Shockwave Flash plugin?

[http://www.discounttire.com/dtcs/interactive.dos](http://www.discounttire.com/dtcs/interactive.dos)

It just shows that I need the plugin even though other flash sites work fine.


Thanks!

If you REALLY want it shockwave to work check out these instructions [http://www.ubuntuforums.org/newreply.php?do=newreply&p=1415318]("http://www.ubuntuforums.org/newreply.php?do=newreply&p=1415318")

It's cobbled together and does not work ALL the time but with Wine, Mozplugger,shockwave, and Firefoxforwindows you have shockwave for your Linux machine.  Whenever you need shockwave mozplugger will tell firefox to use the firefox for windows...should help out.  I can see the wheels on my car;)

---

