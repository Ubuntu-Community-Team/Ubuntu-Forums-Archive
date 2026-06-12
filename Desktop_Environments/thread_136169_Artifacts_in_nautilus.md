---
title: "Artifacts in nautilus"
date: 2006-02-25
forum: Desktop Environments
---

### Post by Ramses de Norre on 2006-02-25
Since I changed my Theme to D3a, I've got a lot of artifacts in nautilus.
I attached a screenshot as an example, but it's even worse sometimes.
What can I do about this? It's pretty ugly and annoying.

---

### Post by Perfect Storm on 2006-02-25
I think you should contact bvc about the problem.

---

### Post by Ramses de Norre on 2006-02-25
What is bvc? The makers of the theme?

---

### Post by Perfect Storm on 2006-02-26
Yes. He is also have an ubuntu forum account with the same name, a PM will be fine.

---

### Post by bvc on 2006-02-28
Thanks for telling me, but I'm not having this problem, so it's hard to fix. I know the sidebar scrollbar in nautilus was bad for a long time, and I and other themers never new why, but I thought this was resolved some time ago. Other themes were effected as well. I'm now on dapper and do not have this problem. Do you Artificial Intelligence?

do you get any errors from a terminal with
nautilus --browser

---

### Post by Ramses de Norre on 2006-02-28
Yes, nautilus --browser opens a nautilus window with a lot of artifacts on the scroll bar..
There is nothing else displayed at the terminal, just a new prompt.

---

### Post by Perfect Storm on 2006-02-28
[QUOTE=bvc]Thanks for telling me, but I'm not having this problem, so it's hard to fix. I know the sidebar scrollbar in nautilus was bad for a long time, and I and other themers never new why, but I thought this was resolved some time ago. Other themes were effected as well. I'm now on dapper and do not have this problem. Do you Artificial Intelligence?
[/QUOTE]

I have only seen the pixilation with one of the scrollers in gimp, but I thought that might be a gimp bug.

---

### Post by bvc on 2006-03-01
Well, I guess get any updates you can for gtk2 and nautilus. I realize it is something with the theme, most likely a class tied to a style that nautilus doesn't like, but I've never figured out which one.

---

### Post by bvc on 2006-03-02
[try this]("http://kwh.kernow-gb.com/~bvc/theme/devel/d3a-TEST.tar.gz") and let me know if it helps

---

### Post by Perfect Storm on 2006-03-02
No still there with gimp, strange it only appear with gimp for me.

---

### Post by Ramses de Norre on 2006-03-02
I've still got the artifacts with this theme, what do you mean by updating nautilus and gtk2? I've got the most recent versions from the repo's.

---

### Post by bvc on 2006-03-02
[QUOTE=Artificial Intelligence]No still there with gimp, strange it only appear with gimp for me.[/QUOTE]That's because it's a diff problem (thx for pointing it out...can you tell I didn't ever use this theme much?) I fixed that. Strange is that some pixmap themes correctly use the horizontal range and others use the range slider with the listheader button as a background :/. D3a unfortunately uses the button, which had bad borders (I was new to gtk when I made it...gimme a break!).

Ramses de Norre asked the mystery question with the vertical nautilus scrollbar (see screenshot above). I think it is because gtk/nautilus can't handle a 9x9 image and stretch it to 14px width in the sidebar (related to a 'TreeView/List/Text' function in gtk???), so I have made new troughs. I can not test the theory so **please let me know if it works, because until it is confirmed I can not update at gnome-look!**

[d3a.tar.gz]("http://kwh.kernow-gb.com/~bvc/theme/gtk/d3a.tar.gz")
get this because on top of fixing the horizontal slider in gimp, it fixes having the same color for fg and base INSENSITIVE, and base active/selected colors which is a no, no. You'll now be able to see the text on insensitive widgets and understand what is selected/active in listviews better! ....ooops (I was new to gtk when I made it...gimme a break!) :D .

---

### Post by Ramses de Norre on 2006-03-03
I think it's fixed:) haven't seen any artifacts yet!

---

### Post by Perfect Storm on 2006-03-04
My problem is also solved :)

---

### Post by bvc on 2006-03-04
Great! Thanks for confirming! That's a year old headache, gone!
[d3a.tar.gz]("http://kwh.kernow-gb.com/~bvc/theme/gtk/d3a.tar.gz")
This one fixes the listheader being used as a range slider background, as posted by AI in the gimp and uses the range slider trough.... and has new listheaders! :p 
[IMG]http://kwh.kernow-gb.com/~bvc/theme/devel/gimp-range-slider-bg.png[/IMG]
I'm going to do a few more usability tweaks, and will post back when I'm done updating a gnome-look.

If you need, or want, to revert to the old for some reason [it's here]("http://kwh.kernow-gb.com/~bvc/theme/gtk/d3aOLD.tar.gz").

---

### Post by bvc on 2006-03-04
[http://www.gnome-look.org/content/show.php?content=15963](http://www.gnome-look.org/content/show.php?content=15963)
or
[http://kwh.kernow-gb.com/~bvc/theme/gtk/d3a.tar.gz](http://kwh.kernow-gb.com/~bvc/theme/gtk/d3a.tar.gz)

------04 March 2006
-fixed bad nautilus --browser side pane scrollbar trough
-fixed listheader from being used as the range slider background, as was seen in The Gimp -Layers Dialog
-fixed tabs
-fixed bad border on listheader
-new listheaders, down arrow prelight, scrollbar and range troughs
-added insensitive range troughs/sliders for usability
-fixed a few usability issues with colors/text
-fixed alignment of the checkbox

....and probably a few other things I'm forgeting

---

