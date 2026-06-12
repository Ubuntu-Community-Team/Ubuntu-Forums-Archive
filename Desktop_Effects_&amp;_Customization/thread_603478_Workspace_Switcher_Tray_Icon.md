---
title: "Workspace Switcher Tray Icon"
date: 2007-11-05
forum: Desktop Effects &amp; Customization
---

### Post by lferree on 2007-11-05
Having a strange issue where there is only one empty square being displayed for the task switcher tray icon.

Before I would have 4 squares, a gray box showing the current desktop, the others appearing empty.

I have columns set to 4.  

I also noticed there's a tiny dot at the top of the square, moving between 4 positions for each desktop.  You have to really squint to see it.

Any ideas?

---

### Post by Liudwik on 2007-11-05
yep. i have the same issue. can't rotate cube because know i have only 2 desktops. and i'm not sure why. maybe due to compiz update. it hapend after restart

---

### Post by lferree on 2007-11-05
Settings /  Preferences / Advanced Desktop Effects Settings

General Options
Desktop Size [Tab]
Horizontal Virtual Size = 4

...will get u the 4 virtual desktops for cube :)

---

### Post by VictorR on 2007-11-05
I think there is no use for Workplace Switcher applet with Compiz. They work in different ways - Compiz's cube is just a wide single desktop for Workplace Switcher, folded in the shape of cube.
Start CCSM and go to General -> Desktop Size. Here:
Horizontal Virtual Size (=4) - is your cube (if equal to 4)
Vertical Virtual Size (=1) - some extra dimensions to the cube, I have no idea how to use it.
Number of Desktops (=1) - is what you are going to switch with Workplace Switcher. You can set it to 4 and get the applet perfectly running with four cube-shaped desktops. For me it is too complicated to be useful.

---

### Post by jslmg on 2007-11-07
I had this problem too. Then, following your hint, VictorR, I fixed it. I wanted to get my window list in the panel to "show windows from all workspaces," but couldn't do it. I also found that I could change workspaces in Compiz with my middle mouse button or wheel, but the switcher in the panel always stayed on the same desktop.

So, the correct settings in Advanced CCSM (Compiz Config Settings Manager) are:
Horizontal Virtual Size = 4
Number of Desktops = 1

That way, I get four functioning desktops, with the panel workspace switcher working in sync with Compiz's workspaces. AND, I get all open windows from all workspaces showing in my panel window list.

Thanks Victor.

---

### Post by jslmg on 2007-11-07
Another bug, though: Some applications do not show up in the Compiz-enabled panel workspace switcher. Right now, I'm running Firefox on desk 2, Thunderbird on desk 2, and CCSM on desk 4. Firefox and CCSM show up in the panel switcher, but Thunderbird does not. I've moved Thunderbird from workspace to workspace, too, and it still doesn't show. However, all else so far seems normal. For example, I can right click on the title bar for an app and move select "Move to another Workspace."

Any other observations about the Compiz/panel switcher issues?

---

### Post by zzarr on 2007-11-07
Hello!

I had the same problem too, but thanks to VictorR's tips it's fine now.

**Thanks VictorR!**

I was a bit frustrated, all this wonderful eye-candy and not being able to use it because of a that small issue.

But now I'm flying around among the desktops doing things a Vista user can't imagine. :)

**Once more, a thousand thanks to you VictorR!**

I hope this issue is fixed in compiz updates.


Greetings
Zzarr

---

### Post by VictorR on 2007-11-07
Thanks everybody, but actually it was not my achievement. The applet did not work for me. It was jslmg who played with it until it worked as expected. When I got his message I started Workspace Switcher again and it now works for me! Thank you jslmg.
I can only guess that matching number of columns in the applet and sides in Compiz's cube did the trick. (When I started the applet first time yesterday it had 2 columns, so I had two cubes in two virtual desktops - one empty and another with my open windows).

Now I can rotate the cube without involving keyboard or screen edges - what I dreamed for long.

So far I have not found other problems with this applet - it shows everything, what I have on the screen. Obviously, hidden windows or covered by others are not shown. And I can't move them on the applet. But if I put a window across two sides on the screen it is shows correctly on the applet.

---

### Post by geezerone on 2008-04-03
I am seeing this too. How exactly is it fixed please? :confused:
[B]
UPDATE:[/B]

Fixed by removing the switcher and adding it again! :)

---

