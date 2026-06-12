---
title: "Help ! Change forum background colour in browser ?"
date: 2006-07-08
forum: Forum Feedback &amp; Help
---

### Post by mips on 2006-07-08
[SIZE=4][COLOR=Red]Please note the forums are in beta phase ! If you follow this thread you have no gaurantee that your changes are permanent !!![/COLOR][/SIZE]
____________________________________________________________
Hi,

Does anybody know how I can get Konq & Firefox/Swiftfox to change the white forum background in my browser to something easier on the eyes.

My eyes are really taking strain with all the white and I will either have to get my browser to change the colour or spend less time here. As it is my eyes are sensitive to bright light, adjusting my monitor is not a solution as it has been colour profiled to render colours as accurate as possible.

Anybody with suggestions ?

---

### Post by adam.tropics on 2006-07-08
In firefox, edit-->preferances-->content-->colors

De-select allow sites to use their own colors, and pick your own.
The cost is high though in the sense that this change is global for all sites you visit. I don't know of a way to do it for just one site, sorry.

---

### Post by adam.tropics on 2006-07-08
Update: I was wrong, it can be done!

Firefox extension [Stylish]("https://addons.mozilla.org/firefox/2108/") can change settings for individual sites, based on exact page, or just domain. It is however not the simplest thing in the world to use, anyway, you can change anything for example....

---

### Post by mips on 2006-07-08
adam.tropics,

I thank you for that information ! I will try the extension shortly.

Thanks again
mips

---

### Post by mips on 2006-07-08
Stylish requires knowledge of CSS which I have zip of.

---

### Post by mips on 2006-07-08
Ok, Stylish does the job just fine thanks to the help from Kassetra on the CSS code.

---

### Post by ahaslam on 2006-07-08
> **mips said:**
> Ok, Stylish does the job just fine thanks to the help from Kassetra on the CSS code.
I've got the brightness turned down here :cool: Could you share your learnings? ;) 

Tony

EDIT: removing sunglasses, we've now got a background shade (that isn't in the ubuntu.com colour palette)!

---

### Post by mips on 2006-07-08
Ok, been using it for a few minutes now and stylish does not seem to behaving as it should. The changes do not seem to be carried over to every  page that gets loaded and there is still a few white spots on the main page and some other places. You should find browsing a thread pleasurable though.

Install the stylish extension, restart firefox, click on the stylish icon installed at the bottom and select 'create style' copy this code, apply and save.

Maybe more people can contribute to it and make it better.

```
@namespace url(http://www.w3.org/1999/xhtml);

@-moz-document domain("www.ubuntuforums.org") {

}

.page { background: #dedecf; color: #000; }

.tborder { background :#dedecf; border: 1px solid #000; }

.alt1 { background: #dedecf; color: #333366; }
```

---

### Post by kassetra on 2006-07-08
> **mips said:**
> The changes do not seem to be carried over to every page that gets loaded and there is still a few white spots on the main page and some other places.


Well, it is actually carrying over, it's just that each new "page" you see has a different dynamically created css "file" for it - based upon what is loaded into the template pieces.... so if you get it set the way you want on one "page" there is no guarantee that the next "page" uses those same css bits.

---

### Post by LKRaider on 2006-07-08
That Stylish thing is great!

I have "improved" (and fixed a bit) the template given by **mips**. Here it is:

```
@namespace url(http://www.w3.org/1999/xhtml);

@-moz-document domain("ubuntuforums.org") {

body { background: #c5c5b6 !important; }

.page { background: #dedecf !important; color: #000 !important; }

.tborder { background :#dedecf !important; border: 1px solid #c5c5b6 !important; }

.panelsurround { background :#F8F8F3 !important; }

.panel { background :#F8F8F3 !important; }

.alt1 { background: #F8F8F3 !important; }

}
```

I also published it at [userstyles.org]("http://userstyles.org/style/show/621"), where you can see a screenshot of the before/after.

---

### Post by benplaut on 2006-07-09
> **LKRaider said:**
> That Stylish thing is great!

I have "improved" (and fixed a bit) the template given by **mips**. Here it is:

```
@namespace url(http://www.w3.org/1999/xhtml);

@-moz-document domain("ubuntuforums.org") {

body { background: #c5c5b6 !important; }

.page { background: #dedecf !important; color: #000 !important; }

.tborder { background :#dedecf !important; border: 1px solid #c5c5b6 !important; }

.panelsurround { background :#F8F8F3 !important; }

.panel { background :#F8F8F3 !important; }

.alt1 { background: #F8F8F3 !important; }

}
```

I also published it at [userstyles.org]("http://userstyles.org/style/show/621"), where you can see a screenshot of the before/after.

oohh, very nice!
it doesn't match with some of the icons that aren't transparent, but that's not a big issue.

very nice :cool:

---

### Post by adam.tropics on 2006-07-09
LKRaider: Nice work! Cheers. Just checked out some of the ones for other sites, there's a lot of nice ones there.

---

### Post by mips on 2006-07-09
> **LKRaider said:**
> That Stylish thing is great!

I have "improved" (and fixed a bit) the template given by **mips**. Here it is:


Thanks, looking good !

Now we just have to catch all the odds and sods that are still white, a tweak here & there and this could be a great stylish theme.

---

### Post by mips on 2006-07-09
> **kassetra said:**
> Well, it is actually carrying over, it's just that each new "page" you see has a different dynamically created css "file" for it - based upon what is loaded into the template pieces.... so if you get it set the way you want on one "page" there is no guarantee that the next "page" uses those same css bits.

Now I understand why it is so difficult/laboriuos to create multiple themes, just so many parameters to change and keep tags on.

Next time someone asks about themes maybe you should point them here ;)

---

### Post by adam.tropics on 2006-07-09
I am pretty sure we could use this to move the search (down and left) any thoughts?

---

### Post by henriquemaia on 2006-07-09
Wow!!! 

Thanks a lot for this thread! Now I can give some peace to my eyes. It's much nicer and usable now (for people with eyes/vision problems).

---

### Post by lazyd2 on 2006-07-09
You saved me, thanks!

---

### Post by tseliot on 2006-07-09
Thanks, it works great now! :D

---

### Post by LKRaider on 2006-07-09
> **adam.tropics said:**
> I am pretty sure we could use this to move the search (down and left) any thoughts?
Try adding this to the code:
```
#masthead input[type=text] { margin-top: 30px !important; }

#masthead input[type=submit] { margin-right: 20px !important; }
```

--

About the transparent images: A solution would be to make really transparent png's and substitute them with the css. It is doable.

About other details: If you can point out exactly what to change, I'm sure we can work it out.

---

### Post by henriquemaia on 2006-07-09
Much better now, LKRaider, thanks.

---

### Post by LKRaider on 2006-07-09
I updated the code to fix some of the forums bugs, like the mis-alignement on the user/message columns and the flickering on links hovering inside messages.

It is at the [userstyles.org](http://userstyles.org/style/show/621) page, if you want to update.

---

### Post by henriquemaia on 2006-07-09
Since this is so useful, wouldn't be nice to post a thread on some more visible area (like the ubuntu cafe) pointing to this one, so that more people know about it? What do you think?

---

### Post by adam.tropics on 2006-07-09
> **LKRaider said:**
> I updated the code to fix some of the forums bugs, like the mis-alignement on the user/message columns and the flickering on links hovering inside messages.

It is at the [userstyles.org](http://userstyles.org/style/show/621) page, if you want to update.

Thanks for that.

---

### Post by LKRaider on 2006-07-09
Hi there again. I made a new update :P

This now replaces the images with correct transparent png versions. Hope you guys like it :D

Again, browse to the [userstyles.org](http://userstyles.org/style/show/621) page to get it.

About the ubuntu cafe idea: do we really need another thread? I think this one is doing fine. But if you want to post there, feel free :)

---

### Post by henriquemaia on 2006-07-09
> **LKRaider said:**
> Hi there again. I made a new update :P

This now replaces the images with correct transparent png versions. Hope you guys like it :D

Again, browse to the [userstyles.org]("http://userstyles.org/style/show/621") page to get it.

About the ubuntu cafe idea: do we really need another thread? I think this one is doing fine. But if you want to post there, feel free :)

Thanks for this update. About my idea - not another thread, just a thread on a **more visible **forum pointing to this one so more people could benefit from your great work. Maybe on the HowTo section (this is kind of an HowTo) or on Ubuntu Cafe forum.

---

### Post by ubuntu-geek on 2006-07-09
> **henriquemaia said:**
> Since this is so useful, wouldn't be nice to post a thread on some more visible area (like the ubuntu cafe) pointing to this one, so that more people know about it? What do you think?
No not really, the template is still beta. The css class names will change before the final product is out. So by using the custom css you are going to make your forum expereience worse in the next weeks and months.

So I don't suggest anyone does this until you see the beta removed from the bottom of this site.. :)

---

### Post by rcarring on 2006-07-10
Would it be rocket science to have a different theme available for members to chose from? I am sure that vBulletin is capabale of offering more than one theme, and thus a possible elmination of the whiteness.

---

### Post by kassetra on 2006-07-10
> **rcarring said:**
> Would it be rocket science to have a different theme available for members to chose from? I am sure that vBulletin is capabale of offering more than one theme, and thus a possible elmination of the whiteness.

Please don't insult us when asking us to do things.  

Please read the following explanations to get an idea of how theming on vbulletin works:
[http://www.ubuntuforums.org/showthread.php?t=211210&page=3](http://www.ubuntuforums.org/showthread.php?t=211210&page=3)
[http://www.ubuntuforums.org/showpost.php?p=1229607&postcount=31](http://www.ubuntuforums.org/showpost.php?p=1229607&postcount=31)
[http://www.ubuntuforums.org/showpost.php?p=1229173&postcount=20](http://www.ubuntuforums.org/showpost.php?p=1229173&postcount=20)

Also, if we were to make alternate themes, they take a lot of time and a lot of effort and when we get posts like this, our motivation to put all that time and effort into making things for people that don't appreciate the work we do slips away rapidly.

And one final note.  We're not about to make alternate themes for a beta-release of the forum software.  When it's final and the theme itself has been finalized, then we'll look into making additional themes.

---

### Post by LKRaider on 2006-07-10
Good point made by the moderators.

There's no use spreading word about things like this if the forums are going to change and cause breakage with it.
Once they reach a stable release then we could proceed to open "user-themes" threads.

**kassetra**: please, don't think we don't appreciate your work, afterall, we can only be here because of what you are all doing for us.
I for one am really impressed with what these forums are capable of, and the way you manage to be constantly evolving them, and I believe many people are too.

---

### Post by ubuntu-geek on 2006-07-10
> **rcarring said:**
> Would it be rocket science to have a different theme available for members to chose from? I am sure that vBulletin is capabale of offering more than one theme, and thus a possible elmination of the whiteness.
Hmm since you put it so rude.. NO..

---

### Post by mips on 2006-07-10
> **ubuntu-geek said:**
> No not really, the template is still beta. The css class names will change before the final product is out. So by using the custom css you are going to make your forum expereience worse in the next weeks and months.

So I don't suggest anyone does this until you see the beta removed from the bottom of this site.. :)

Added a warning to my initial post so people don't get to excited ;)

---

### Post by henriquemaia on 2006-07-10
> **ubuntu-geek said:**
> No not really, the template is still beta. The css class names will change before the final product is out. So by using the custom css you are going to make your forum expereience worse in the next weeks and months.

So I don't suggest anyone does this until you see the beta removed from the bottom of this site.. :)

Thanks for your very clear reply. Ok, time to forget this idea until stable.

---

### Post by henriquemaia on 2006-07-10
> **kassetra said:**
> Please don't insult us when asking us to do things.  

Please read the following explanations to get an idea of how theming on vbulletin works:
[http://www.ubuntuforums.org/showthread.php?t=211210&page=3](http://www.ubuntuforums.org/showthread.php?t=211210&page=3)
[http://www.ubuntuforums.org/showpost.php?p=1229607&postcount=31](http://www.ubuntuforums.org/showpost.php?p=1229607&postcount=31)
[http://www.ubuntuforums.org/showpost.php?p=1229173&postcount=20](http://www.ubuntuforums.org/showpost.php?p=1229173&postcount=20)

Also, if we were to make alternate themes, they take a lot of time and a lot of effort and when we get posts like this, our motivation to put all that time and effort into making things for people that don't appreciate the work we do slips away rapidly.

And one final note.  We're not about to make alternate themes for a beta-release of the forum software.  When it's final and the theme itself has been finalized, then we'll look into making additional themes.

Please do not forget that most of us aren't aware of the huge amount of time and effort you put behind this forum. That is not self-evident. Only those behind it know the real difficulty they're facing.


ps: Thanks for all your effort in keeping this site running and providing this wonderful meeting point for our community.

---

