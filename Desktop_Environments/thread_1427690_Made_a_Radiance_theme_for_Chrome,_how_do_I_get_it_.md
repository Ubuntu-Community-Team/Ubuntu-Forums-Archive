---
title: "Made a Radiance theme for Chrome, how do I get it included with Chromuim in the repos"
date: 2010-03-11
forum: Desktop Environments
---

### Post by mazz0 on 2010-03-11
OK, so I made [a radiance theme for Chrome ]("http://gnome-look.org/content/show.php/Radiance+Chrome+Theme?content=121276") and will make an Ambiance one soon.  Assuming one of these two themes is the default when Lucid goes final, I figure it'd be nice if the matching theme was the default when you install Chromium from the repo.  So... how would I go about arranging that?

---

### Post by bruno9779 on 2010-03-11
That looks nice!

I dunno the answer to your question though...

---

### Post by mazz0 on 2010-03-11
Yeah, I really like Radiance - it's made me a bit less dissapointed about RGBA being postponed!  And I like the purple background too, all looks a lot nicer than the old browns.

---

### Post by wayward on 2010-03-12
Heh, I've just finished my own take on Chrome Radiance.

[IMG]http://gnome-look.org/CONTENT/content-pre1/121457-1.png[/IMG]

I'll leave it here for people who stumble across the thread.

---

### Post by mazz0 on 2010-03-12
Hey Wayward - if you put it in Use System Titlebar and Borders mode, did you find a way to make the tabbar match the system titlebar when it's not the active window?  Chromium seems to ignore the inactive menu-bar entry for me.

---

### Post by wayward on 2010-03-12
You can't easily do that.  Chrome tints inactive frame with the "frame_inactive" tint whether we like it or not, which makes getting the right color nigh impossible.  Also, the frame around the window is drawn using the "frame_inactive" color, which ISN'T tinted for the purposes of drawing the border.

---

### Post by tareksobh on 2010-03-12
What a beautiful theme. Well done... I also don't know how to arrange for it to become the default theme for the installed Chromium, but why don't you start and upload it in the [Google Chrome Extensions]("https://chrome.google.com/extensions") website? Maybe it could gain recognition there, and set itself up from there. That's all I could think off right now. Good luck and looking forward for the Ambiance theme.

---

### Post by MichealH on 2010-03-12
> **wayward said:**
> Heh, I've just finished my own take on Chrome Radiance.

[IMG]http://gnome-look.org/CONTENT/content-pre1/121457-1.png[/IMG]

I'll leave it here for people who stumble across the thread.

I will sigg it.Well, This tread!

---

### Post by tobiash on 2010-03-13
Because I prefer using Chrome with native window decorations, I made two Chrome themes to match Radiance and Ambiance colors.

Radiance:
[IMG]https://chrome.google.com/extensions/img/nhcggnkgnnjofaalfnbdfhkejpjolbce/1268352042.47/screenshot/1[/IMG]
[https://chrome.google.com/extensions/detail/nhcggnkgnnjofaalfnbdfhkejpjolbce](https://chrome.google.com/extensions/detail/nhcggnkgnnjofaalfnbdfhkejpjolbce)

Ambiance:
[IMG]https://chrome.google.com/extensions/img/elnmibmpefhmfgphdphdncoogpbfmlbp/1268352103.62/screenshot/1[/IMG]
[https://chrome.google.com/extensions/detail/elnmibmpefhmfgphdphdncoogpbfmlbp](https://chrome.google.com/extensions/detail/elnmibmpefhmfgphdphdncoogpbfmlbp)

and finally some matching scrollbars (without, Chrome uses something very boxy):
[https://chrome.google.com/extensions/detail/mikdfeaeaecoffpjoodiihgejnbfigln](https://chrome.google.com/extensions/detail/mikdfeaeaecoffpjoodiihgejnbfigln)

I'll update the scrollbars to match the latest "light-themes" from Lucid very soon.

Keep in mind, these are made to use with the native decorations. If you want to use the Chrome decorations, waywards theme might be a better fit.

Regards,
Tobias

---

### Post by Bochonok on 2010-03-13
> **tobiash said:**
> Because I prefer using Chrome with native window decorations, I made two Chrome themes to match Radiance and Ambiance colors.

Radiance:
[IMG]https://chrome.google.com/extensions/img/nhcggnkgnnjofaalfnbdfhkejpjolbce/1268352042.47/screenshot/1[/IMG]
[https://chrome.google.com/extensions/detail/nhcggnkgnnjofaalfnbdfhkejpjolbce](https://chrome.google.com/extensions/detail/nhcggnkgnnjofaalfnbdfhkejpjolbce)

Ambiance:
[IMG]https://chrome.google.com/extensions/img/elnmibmpefhmfgphdphdncoogpbfmlbp/1268352103.62/screenshot/1[/IMG]
[https://chrome.google.com/extensions/detail/elnmibmpefhmfgphdphdncoogpbfmlbp](https://chrome.google.com/extensions/detail/elnmibmpefhmfgphdphdncoogpbfmlbp)

Hm, your and wayward's theme have common issue: selection color, it's chrome/chromium blue, not native.

and finally some matching scrollbars (without, Chrome uses something very boxy):
[https://chrome.google.com/extensions/detail/mikdfeaeaecoffpjoodiihgejnbfigln](https://chrome.google.com/extensions/detail/mikdfeaeaecoffpjoodiihgejnbfigln)

I'll update the scrollbars to match the latest "light-themes" from Lucid very soon.

Keep in mind, these are made to use with the native decorations. If you want to use the Chrome decorations, waywards theme might be a better fit.

Regards,
Tobias
Your themes and wayward's one have a common issue: using chrome/chromium blue selection color instead of native one.

---

### Post by tobiash on 2010-03-13
> **Bochonok said:**
> Your themes and wayward's one have a common issue: using chrome/chromium blue selection color instead of native one.

Good idea! The theming API can't do this. Luckily, it's possible to style selections using CSS. To try it out, I added such a rule to my scrollbar customization, which also uses CSS. Eventually, this could be extended to a general customization plugin. You can find the modded version at [my Google-Code project]("http://code.google.com/p/chrome-ubuntu-themes/downloads/detail?name=light-themes-scrollbar.crx&can=2&q="). I did not yet put this to the extension gallery, as it's possible that it collides with other CSS on some webpages and yields unreadable text.

Using the same technique, it should also be possible to style form elements like buttons etc.

---

### Post by River444 on 2010-04-30
Bro this theme is awesome!
Thanks a ton. I was wondering if someone had and sure enough! 
Great quality. 
Perfect Match 
Thanks again :) 
:popcorn::guitar:

---

### Post by captainmnb on 2010-05-01
Tried to download the Ambiance theme, but Google says it's been removed.  Anybody know what's up or know of another place to get an Ambiance theme?

---

### Post by ToxicBurn on 2010-05-01
yeah i need this theme also what happend ?

---

### Post by phibxr on 2010-05-01
> **ToxicBurn said:**
> yeah i need this theme also what happend ?

Actually, this would seem to be the case with MANY themes over at that site.

---

### Post by ToxicBurn on 2010-05-01
:( thats sad that theme really makes chrome look nice if anyone has it can you share please

---

### Post by phibxr on 2010-05-01
> **ToxicBurn said:**
> :( thats sad that theme really makes chrome look nice if anyone has it can you share please

Would love to see this theme posted here too, since no user made Chrome themes are available anymore from Google's own site.

---

### Post by Elric27 on 2010-05-01
[http://mac.softpedia.com/progDownload/Radiance-Theme-Download-76095.html](http://mac.softpedia.com/progDownload/Radiance-Theme-Download-76095.html)

[http://www.soft4000.com/windows/download-ambiance-theme-010-free/](http://www.soft4000.com/windows/download-ambiance-theme-010-free/)

---

### Post by ToxicBurn on 2010-05-01
thank you very much

---

### Post by ToxicBurn on 2010-05-01
I wonder whats wrong with google's site and all the theme links not working

---

### Post by phibxr on 2010-05-02
The google theme site is up again. :)

---

