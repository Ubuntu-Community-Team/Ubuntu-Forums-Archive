---
title: "My desktop manager is broken"
date: 2009-01-05
forum: General Help
---

### Post by Rosver on 2009-01-05
:( I enjoy having xubuntu on my laptop. Then one day something terrible happened. I turned it on. Then I had the feeling that something is wrong. Then I found it! The top and bottom panels are gone without a trace. This thing happened to me too long ago. I had ubuntu then when the same thing happens. I solved it by installing xubuntu over ubuntu.

When I thinker around I found other things that also went wrong:
 - I can't access panels from the settings manager. clicking on the icon does not show any visible effect. I also notice a similar one in my ubuntu problem.
 - The Terminal (from accessories) does not accept the arrow buttons properly. Instead it shows [[A^ , [[B^, [[C^, and [[D^ instead.
 - Thunar show the contents as "detailed list view" every time I open one even if I set it to other kind of views before, whether the previous one still open or not. This is not its behavior before this mess comes up.
 - When I go to other accounts( I had multiple accounts in my laptop, they are still working fine), then use "switch user" to access the damaged account, the panel mysteriously appears but other things that went wrong aren't corrected.
 - I had problems with my optical drive. I can't play movies and music with it anymore.
 - When I open files from other programs like Geany, Abiword, or Gimp. The Hidden files are shown. This could be corrected easily by dis selecting "show hidden files" but it would revert back if restarted.


This is really troublesome. I wonder if this is caused by a bug or a malicious program. I don't submit a bug report because maybe its not caused by a bug but some malicious programs or something entirely different.

Here are other information that may be helpful:
 - The damaged account has administrative permissions and used often. I had two more accounts one is a desktop user accounts,does not have administrative powers, the other is an administrative account but used infrequently, both accounts are still good. The same problem in ubuntu is also in similar conditions, an administrative account that is frequently used
 - This problem appear even without internet connections. The first one (ubuntu) appears while I was connected to a network thats why I thought it was a virus, and I install xubuntu to solve it. But this time, it occurs after I had no connections for a week, that is why I think it is possibly a bug.
 - this might be caused by some other programs independent of the desktop manager for in both desktop manager the same thing happened.
 - Seemingly all other programs work well.

---

### Post by bumanie on 2009-01-05
In terminal try > sudo apt-get  --reinstall xubuntu-desktopIf that doesn't work, post back and you may have to uninstall and then reinstall the xubuntu-desktop.

---

### Post by Rosver on 2009-01-06
Sorry but it does not. When I enter it at my terminal and give my password it just say

    E: Invalid operation xubuntu-desktop

---

