---
title: "No text in MythTV"
date: 2009-05-31
forum: General Help
---

### Post by BrownCoal on 2009-05-31
Hi,

MythTV is not displaying any text on the frontend or the backend.
I took three screenshots:

1. [[COLOR="Blue"]_http://i626.photobucket.com/albums/tt348/89f5hb/MythTV_no_text_bug_screenshot_1.jpg_[/COLOR]]("http://i626.photobucket.com/albums/tt348/89f5hb/MythTV_no_text_bug_screenshot_1.jpg")
2. [[COLOR="Blue"]_http://i626.photobucket.com/albums/tt348/89f5hb/MythTV_no_text_bug_screenshot_2.jpg_[/COLOR]]("http://i626.photobucket.com/albums/tt348/89f5hb/MythTV_no_text_bug_screenshot_2.jpg")
3. [[COLOR="Blue"]_http://i626.photobucket.com/albums/tt348/89f5hb/MythTV_no_text_bug_screenshot_3.jpg_[/COLOR]]("http://i626.photobucket.com/albums/tt348/89f5hb/MythTV_no_text_bug_screenshot_3.jpg")

I did a Google search for [[COLOR="Blue"]_mythtv "no text"_[/COLOR]]("http://www.google.com.au/search?hl=en&q=mythtv+%22no+text%22&btnG=Google+Search&meta=&aq=f&oq=") and it seems to be a problem for numerous people. Four pages where particularly relevant:
1. [http://ubuntuforums.org/showthread.php?t=394436#2](http://ubuntuforums.org/showthread.php?t=394436#2)
2. [http://www.mythtvtalk.com/forum/installation-issues/4400-newbie-help-qt-opengl-now-no-text-menu.html](http://www.mythtvtalk.com/forum/installation-issues/4400-newbie-help-qt-opengl-now-no-text-menu.html)
3. [https://help.ubuntu.com/community/MythTV/FAQs#Troubleshooting](https://help.ubuntu.com/community/MythTV/FAQs#Troubleshooting)
4. [https://lists.ubuntu.com/archives/universe-bugs/2009-March/061860.html](https://lists.ubuntu.com/archives/universe-bugs/2009-March/061860.html)

I installed msttcorefonts but it didn't help. I tried the command "mythfrontend -O ThemePainter=qt" but it didn't fix it. I then tried "mythfrontend -O ThemePainter=openGL" and I was finally able to see the main menu of MythTV, but all of the configuration menus are still blank.

I have a (legacy) ATI Radeon 9600. Jaunty doesn't have a proprietary ATI legacy driver so I must use the open-source one. I think this may be a cause of the problem because when I used the proprietary driver in Intrepid Ibex the text was visible.

Does anyone have a solution?

P.S. Why aren't links differentiated from plain text? I had to highlight and underline the links manually.

---

### Post by BrownCoal on 2009-05-31
Solved.

The solution is to open the file /etc/mythtv/session-settings as sudo and add the text (excluding square brackets) [export XLIB_SKIP_ARGB_VISUALS="1"] at the bottom. (found on the bug report here: [https://bugs.launchpad.net/ubuntu/karmic/+source/mesa/+bug/341898/comments/102](https://bugs.launchpad.net/ubuntu/karmic/+source/mesa/+bug/341898/comments/102))

The first proposed solution was to add the line (excluding square brackets) [Option "DRI" "off"] into the file /etc/X11/xorg.conf under the 'Device' section. This approach makes text visible but it disables DRI, which disables hardware acceleration and makes MythTV run almost unusably slow. (Info from here: [http://ubuntuforums.org/showthread.php?t=1154240](http://ubuntuforums.org/showthread.php?t=1154240))

This problem SHOULD be fixed in Ubuntu Karmic Koala, set for release in October 2009.

---

