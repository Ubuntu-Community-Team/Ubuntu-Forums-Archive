---
title: "Transluency Like Vista"
date: 2008-01-01
forum: Desktop Effects &amp; Customization
---

### Post by diwas on 2008-01-01
Let me get straight to the topic. I want to have the translucent effect in the title bar like MS-Vista has. The theme is named as aero theme in that OS. Can i have that in my system? And How? 
In addition to that, i want to have the whole window including the title bar of course. So what do i have to do for that?
Thank you.

---

### Post by snakeeyes on 2008-01-01
Hi, if u have emerald theme manager installed then u can use it while running compiz fusion.

"sudo apt-get install emerald"

You can download many Windows Vista Aero themes from:

[http://www.gnome-look.org](http://www.gnome-look.org)

---

### Post by diwas on 2008-01-01
Thank you for replying, yes i have emerald.
Does it have translucent thing? I mean we can make the title bar transparent easily but iam talking about tranlucent. Is it possible?
The transparent theme works fine in my system (64MB graphics card, 512MB RAM) will the translucent work too?
Can you please post some good aero theme download links incase i cannot find them.
Thank you.

---

### Post by FuturePilot on 2008-01-01
GTK theme
[http://www.gnome-look.org/content/show.php/Aero-clone?content=57352]("http://www.gnome-look.org/content/show.php/Aero-clone?content=57352")
Emerald theme
[http://www.gnome-look.org/content/show.php/Vista-Linux?content=42875]("http://www.gnome-look.org/content/show.php/Vista-Linux?content=42875")
Icons
[http://www.gnome-look.org/content/show.php/nuoveXT+2?content=56625]("http://www.gnome-look.org/content/show.php/nuoveXT+2?content=56625")

For the GTK and icon themes just drag and drop the archives into the Appearance window. System>Preferences>Appearance
For Emerald open the Emerald Theme Manager (System>Preferences>Emerald Theme Manager) and click Import.

---

### Post by snakeeyes on 2008-01-01
Sorry for the late reply but yeah u can set it to be translucent by editing theme settings in emerald.

---

### Post by diwas on 2008-01-01
Thank you for your links.
Ok, from where can i make my title bar translucent in emerald? I saw only the transparent option coming up.

---

### Post by snakeeyes on 2008-01-01
You will have to adjust it on ur own depending on the theme u r using, as long as it isn't using pix maps u can adjust its transperency.

---

### Post by oedipuss on 2008-01-01
I'm guessing you mean the blurred look behind transparent parts. 
For that you must enable the blur plugin from compiz and set it up to your liking. Don't forget to add window types to the "Alpha blur windows" text field in CCSM (setting it to 'any' without the quotes would do the job). I'm mentioning this because for some reason it was blank by default for me, and it's easy to overlook it. 
Then go to emerald theme manager, select the tab "Emerald Settings" and set the "Compiz Decoration Blur Type" to 'All decoration' or 'Title only' . Then you just choose your favourite theme with transparency, and everything behind it is blurred.

PS: You can select various blur types/strengths from CCSM's blur settings, to better match vista.

Just to clarify (if that's indeed what you mean) :
 There's no difference between transparency and translucency in compiz or emerald. They both come under transparency which can be partial or total. The blur plugin actually just blurs everything behind a window or decoration with partial transparency.

---

### Post by diwas on 2008-01-02
Hey thank you for the information. I will try it in my system ASAP. 
Thank you again for the information.

---

### Post by Saint Angeles on 2008-01-02
i read an interesting article the other day about an advancement in the Murrine GTK engine that allows for transparency in the entire window (not just the titlebar, and not the words and buttons... just the normally grey part changes... like in vista)

they haven't released it yet. i bet its because they're jerks. jk

i love the glassy Murrine themes

---

### Post by PinkFloyd102489 on 2008-01-02
[http://gnome-look.org/content/show.php/Complete+Vista+Aero+theme+%28automated%29?content=72318](http://gnome-look.org/content/show.php/Complete+Vista+Aero+theme+%28automated%29?content=72318)


There's a Vista theme that I compiled. Feel free to take the Emerald theme from it.

---

### Post by diwas on 2008-01-03
Yeah this is the Vista theme...but not the translucent title bar. I am so much dyin for that...

---

### Post by meindian523 on 2008-01-03
Not hijacking the thread,but how can I use transparency for the tooltips and menus without emerald?I earlier had installed C-F from Vorian's repos(IIRC) and all the tooltips and menus were transparent(and I could adjust the level of transparency using a slider in General options) but that doesn't exist in the new C-F I installed using Forlong's guide.How do I get that back?

FYI:
Using Flat-File configuration backend instead of gconf following instructions on Forlong's blog,if that makes any difference.

---

### Post by diwas on 2008-01-03
Well mate no idea, coz i dont like the complete transparent stuff.....sorry

---

### Post by PinkFloyd102489 on 2008-01-03
[http://gnome-look.org/content/show.php/SubVista?content=66075](http://gnome-look.org/content/show.php/SubVista?content=66075)


How about that? That's the Emerald theme that I use.

---

### Post by diwas on 2008-01-03
Hehe sorry but the titlebar is still transparent not TRANSLUCENT.

---

### Post by snakeeyes on 2008-01-03
Try this:

[http://gnome-look.org/content/show.php/White+Vista?content=64252](http://gnome-look.org/content/show.php/White+Vista?content=64252)

---

### Post by peitschie on 2008-01-03
diwas, it is obvious people ARE NOT understanding your definition difference between transparent and translucent.
[B]
For all those who are struggling (like me) understand the difference diwas is trying to indicate:

transparent - entirely see-through, like a normal piece of glass
translucent - something closer to frosted glass. See [http://shellrevealed.com/photos/blog_images/images/243/590x480.aspx](http://shellrevealed.com/photos/blog_images/images/243/590x480.aspx) for an example[/B]

diwas, you keep stating that every single theme people have mentioned doesn't have "translucency"... have you tried enabling the blur plugin and adjusting the transparency as some other posters have recommended?  If so, what was wrong with the results?  Can you make it clearer why the themes don't meet your needs?

As far as I can tell, things like this: [http://www.gnome-look.org/content/preview.php?preview=1&id=72318&file1=72318-1.jpg&file2=&file3=&name=Complete+Vista+Aero+theme+%28automated%29](http://www.gnome-look.org/content/preview.php?preview=1&id=72318&file1=72318-1.jpg&file2=&file3=&name=Complete+Vista+Aero+theme+%28automated%29) , duplicate the look you are talking about.  As already stated, you can adjust the blur window plugin in compiz, and the titlebar transparency in emerald to make the background more "frosted"

---

### Post by PinkFloyd102489 on 2008-01-03
That's why I posted that, that's the theme that I made. Looks good on my computer, no?

---

### Post by rainwalker on 2008-01-03
> **diwas said:**
> Hehe sorry but the titlebar is still transparent not TRANSLUCENT.

People aren't understanding what you mean by "translucent". I'm guessing you mean the blurry frosted glass look, and you do that by enabled Compiz's Blur plugin.

---

### Post by diwas on 2008-01-04
Yes, thank you...its stuff kind of frosted glass. But where is the blur effect in compiz? i cannot get it...pardon me if this is a simple question coz iam totally newbie to linux.

---

### Post by PinkFloyd102489 on 2008-01-04
If you have compizconfig-settings-manager installed, it's in there.

---

### Post by rainwalker on 2008-01-04
> **diwas said:**
> Yes, thank you...its stuff kind of frosted glass. But where is the blur effect in compiz? i cannot get it...pardon me if this is a simple question coz iam totally newbie to linux.

You have to install the package compizconfig-settings-manager (you can do that with Synaptic), and it will be put under System > Preferences > Advanced Desktop Effects Settings.

---

### Post by peitschie on 2008-01-04
Hi diwas,

It's cool to be a linux n00b ;)... we all were at some point in time.  To install the extra compiz plugins, open a gnome terminal (Applications > Accessories > Terminal), and enter the following command:
```

sudo apt-get install compiz-fusion-plugins-extra compiz-fusion-plugins-main compizconfig-settings-manager compiz-plugins

```

This will install the various compiz plugin packages, and the compizconfig-settings-manager which can then be used to control the settings.  Then you can follow the advice from the previous post and open up the compizconfig-settings-manager package via System > Preferences > Advanced Desktop Effects Settings.  If you type "blur" in the "Filter" text box on the left-hand side, it should limit it so you can just see the blur window filter.

Once you have found this, click on it, and in the "Focus blur windows" enter the value "any" (without the quote marks).  I'm just writing this off the top of my head, so if someone has clearer instructions please post them :)...  If this doesn't work straight away diwas, please tell us so we can walk you through it!

Hope it all works :)

---

### Post by diwas on 2008-01-05
Actually, beside the Focus blur windows there is no field i mean there is no text field. Below that there is alpha blur window...this has text field. So what amI to do now? Is it because i have low graphics card...Intel integrated 64MB graphics card.
HELP!!!!!!

---

### Post by diwas on 2008-01-09
C'on guys please help me. I cant get the blur effect in the titlebar. I did select the titlebar only in Emerald. But nothing is workin. And why have you guys stopped replyin??? Please help me.

---

### Post by peitschie on 2008-01-09
Hi diwas,

Unfortunately I don't have much more to add, hence why the replying has stopped.  Try putting 'any' (without the quote marks) in any text fields you have and such in the blur window plugin.  I don't understand why it isn't giving you more options however.  Are you running Ubuntu 7.10 (Gutsy)?

---

### Post by rune0077 on 2008-01-09
type "any" (minus the quotes) in the Alpha blur windows text field. That should do the trick.

---

### Post by diwas on 2008-01-10
I did that in the text field. I mean i typed any in all the text field available in the blur option, but it is not bluring anything. Yes iam using 7.1
Here is the screenshot.

---

### Post by rune0077 on 2008-01-10
Okay, try this:

- uncheck Focus blur

- Change blur filter to Gaussian

- Set Gaussian strength and Gaussian radius to maximum

This is how mine is set, and it works on my end of things. Hope it helps.

---

### Post by diwas on 2008-01-10
It still did not work out! I'am attaching the new setting's screenshot again, includin the emerald's.

---

### Post by rune0077 on 2008-01-10
I think what you need to do, is edit the Emerald theme. In Emerald Theme Settings, hit the Edit Theme tab and from here, click on the "Select Engine" (just select the engine it's already set for). Now you'll have a list of settings - try playing around with the opacity settings for some/all of these - I think, the higher you set the opacity, the more blurry the blur effect will be.

Not sure if this will work, but I can't really see what should be wrong with your settings. They're set exactly as mine in Compiz and I get the effect, so I'm guessing it has to be Emerald.

---

### Post by diwas on 2008-01-10
Hmm i tried a lot, increasing of opacity just overlays the color...so its not kinda blur...
I dont know what is wrong here.
Did the opacity increasing works for you to get a good blur, not the color overlay thing?

---

### Post by rune0077 on 2008-01-10
Not sure exactly how I got it (I've been fiddling so much with Emerald that I'm no longer sure what I did and didn't do). 

I'm using the True Glass frame engine and most of the opacity options are set to between 40-50.

---

### Post by oedipuss on 2008-01-10
Check the 'Emerald Settings' tab in emerald theme manager. At the bottom of the options there, you should see a 'Compiz Decoration Blur Type' listbox. Change that to 'All Decoration'. This should enable blur for decorations too. Decorations are the frame and title bar around the windows, and are considered a different part of the window. 
Here's what to look for :[IMG]http://i54.photobucket.com/albums/g104/azathothgr/Screenshot.jpg[/IMG]

It should work, but try restarting compiz too, after you've enabled the blur plugin. 
Hope this helps =) If it doesn't, I'm out of ideas :P

---

### Post by rikai on 2008-01-10
This one is easy. 
1. Open Compiz settings(**System > Advanced > Advanced Desktop Effect Settings**).
2. Check the box to enable the **blur** plugin.
3. Open Emerald theme manager(**System > Preferences > Emerald Theme Manager**).
4. Go to the **Emerald Settings** tab.
5. In the dropdown beside **Compiz Decoration Blur Type** select **All Decoration**.
6. Press **quit**.
7. Click on the button for **blur**.
8. Be sure the box for **Alpha Blur** is checked.
9. Under Blur filter select **Gaussian**.
10. **Gaussian Radius** and **Gaussian Strength** will control the blur effect, tweak it to your liking.

Glad i could help. :)

---

### Post by diwas on 2008-01-11
Both the ideas did not work out. Maan what is the problem with this? Is it because of my graphics card?? 64MB Integrated Intel. (iam repeatin this again).
Any new idea?
Thank you.

---

### Post by durand on 2008-01-11
I'm pretty sure its to do with your graphics card. I have an intel integrated 945 and blur was one of the few things that didn't work with it. It just doesn't have OpenGL bindings or something like that.

---

### Post by CarpKing on 2008-01-11
It probably is your video card.  I think blur only works on higher-end cards.  This does not include mine, a 64mb Radeon 9600.  I'm not sure if it was a deficiency in the drivers or in the hardware, but I know blur doesn't work for me (or at least it didn't; it always crashed beryl and I don't recall trying it since).  EDIT: Just tried it, and is seems to have the same effect as the OP's attempts- nothing.  They should really implement a check to tell you if certain plugins won't work with your hardware, although not doing anything is probably better than the crashes it used to do.

---

### Post by diwas on 2008-01-12
Hmm that means i will not have blur effect in my system until and unless i change my video driver...crap!!! The transparent thing works, then y is the blur thing not working?? Damn! Iam really upset and worst of all i cannot change my graphics card coz I DONT HAVE AN AGP SLOT!! what a masterpiece board!!
Damn!

---

### Post by durand on 2008-01-12
transparency uses different binds to blur, and blur requires a hell of a lot more graphics processing.

---

### Post by diwas on 2008-01-12
Is it?? I honestly didnt know that. Damn...Iam purely unable to make my desktop look like Vi$ta, leave apart better than it. 
But anyways, transparent titlebar are good too...what can i say more? :-(

---

### Post by CarpKing on 2008-01-12
> **diwas said:**
> Damn...Iam purely unable to make my desktop look like Vi$ta, leave apart better than it.

Well, just because there's one effect that Vista does that you can't doesn't mean you should give up on making it look better than Vista.  ^_^

---

### Post by diwas on 2008-01-13
Yeah thats the fact too..
By the way, how do i check whether my system supports 3D or not...i mean the thing required to make a 3D box like thing in Compiz.
Do i need to install separate driver or smthg for that?

---

### Post by Pitxyoki on 2008-01-13
> **diwas said:**
> By the way, how do i check whether my system supports 3D or not...
[QUOTE="[Gentoo's Hardware 3D Acceleration Guide](http://www.gentoo.org/doc/en/dri-howto.xml#doc_chap4)"]```

$ glxinfo | grep rendering
direct rendering: Yes
(If it says "No", you don't have 3D acceleration.)
```[/QUOTE]

"Google is your friend"

---

### Post by diwas on 2008-01-13
It says Yes. Now which plugins in compiz can i use? And how is that 3D effect is turned on and how to see it. 
Waiting eagerly for ur replies.

---

### Post by peitschie on 2008-01-13
Your not the only one suffering diwas:

[http://ubuntuforums.org/showthread.php?t=575023](http://ubuntuforums.org/showthread.php?t=575023)
[http://ubuntuforums.org/showthread.php?t=583708](http://ubuntuforums.org/showthread.php?t=583708)

It seems its related to the Intel drivers... you may just have to live without blur for a few months.  A few people are saying this might be improved in later revisions of Compiz, but unfortunately for now there is nothing that can be done it seems.

---

### Post by Pitxyoki on 2008-01-13
> **diwas said:**
> It says Yes. Now which plugins in compiz can i use? And how is that 3D effect is turned on and how to see it. 
Waiting eagerly for ur replies.

Why don't you just try them and check by yourself?

---

### Post by diwas on 2008-01-14
Hehe nice one!! But u know what...i enabled many plugins but i dont know where it is used. For example, the shift changer i didnt know that it was activated when i press windows key+tab. I knew it accidently.
Oh yes, if there is some link sayin that what each plugin does then it would be a matter of great help.
hehe yes...there are many ppl like me.....hehehe iam relieved now!! :-(

---

### Post by diwas on 2008-01-15
I have 3D Acceleration. Now tell me what exactly is OpenGL? In my assumption it is software renderer for graphics intensive activities, mostly 3D things. And is it graphics card dependent software? How do I install it? If you need more hardware specimen i will give you.

---

### Post by rune0077 on 2008-01-15
Yes, OpenGL is graphics-rendering software, primarily for 3D animation. Think of it as a poor-man's DirectX, but still fully capable of doing what you want your Linux system to do. And yes, it's dependent on hardware: your graphic-card must be able to support it. It very likely does, since all cards more or less do, so the real question is whether Linux supports your card or not. But if you can get transparency and desktop effects to function, then it's working.

---

### Post by diwas on 2008-01-17
I got it installed in my system. And i think it works. And yeah i saw the 3D cube thing through Compiz. Is it the cube plugin? And how to activate it, i mean how to see the 3D cube in the desktop.

---

### Post by rune0077 on 2008-01-17
Yeah, once the cube-plugin is activated, you should have a cube desktop. You also need to make sure you have at least four workspaces or the cube won't work. Finally, you should activate the Rotate Cube plugin, so you can actually see the cube rotating when you change desktops. You can fiddle with the settings in these two plugins to get everything to your liking.

---

### Post by diwas on 2008-01-17
Yes its working! But what i actually wanted is that the 3D box shows up in the desktop. Like a cube type of thing. Where actually there are the workspaces. How is it possible?

---

### Post by diwas on 2008-01-17
Oh the zoom setting does that!! Hehe. Tell me what is that cube cap thing?

---

### Post by ronmarley1 on 2008-01-17
> **diwas said:**
> Oh the zoom setting does that!! Hehe. Tell me what is that cube cap thing?

Cube Cap allows you to have an image on the top and bottom of the cube.  See the screenshots below of mine.

---

### Post by diwas on 2008-01-17
Hey thank you. I know how to change it ie the cap picture. But how to see it in the desktop?

---

### Post by diwas on 2008-01-17
And yes how to take screenshot during the Cube Effect and woble effect?

---

### Post by Pitxyoki on 2008-01-17
Do you even know how to search for your answers before posting everything you think of?

---

### Post by ronmarley1 on 2008-01-17
> **diwas said:**
> Hey thank you. I know how to change it ie the cap picture. But how to see it in the desktop?

Use <Ctrl><Alt>Left mouse button to zoom the cube out and move the mouse to manipulate the cube.

---

### Post by ronmarley1 on 2008-01-17
> **diwas said:**
> And yes how to take screenshot during the Cube Effect and woble effect?

There's a few ways to take a screenshot while the cube is enabled or while a window is wobbling, although a screenshot of wobble is usually "torn" for me.

One way: use Gimp.  File, Acquire, Screenshot.  Tick the radio button in front of Whole screen and set the delay for a few seconds.

Another way: use gnome-screenshot.  Typing ```
gnome-screenshot --delay 5
```
in a terminal will take a screenshot after 5 seconds.  Change the number, change the time.

Another way: Applications, Accessories, Take Screenshot.  You can adjust the time in this window.

---

### Post by diwas on 2008-01-18
Ok Pitxyoki thank you for suggesting me to search before i post. But i have enough sense for that. Sorry if these words were harsh. I tried searching but it never displays the result. Yes the key words used was short and relevant, but no result is shown. So what can i do? Well i dont know what problem is this but Iam facing it. Yeah when i try making a new post, it shows many topics of the same thing i want. 
I try searchin everything before i ask here but what can i do??

---

### Post by diwas on 2008-01-18
Thank you for the terminal code...i really wanted that instead of the graphical things. The cube effect is cool, i really like this on top of everything.
Now i dont think i can ask question any further....(sorry if those were irritating)
Thank you.

---

