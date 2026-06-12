---
title: "regnum online"
date: 2006-12-01
forum: Gaming &amp; Leisure
---

### Post by MaximB on 2006-12-01
I don't know if you know this cool game , but it has an unofficial Linux client and it's free.

[http://www.regnumonline.com.ar/eng_site/](http://www.regnumonline.com.ar/eng_site/)
Linux native client how to :
[http://www.regnumonline.com.ar/forum/showthread.php?t=1617&highlight=linux](http://www.regnumonline.com.ar/forum/showthread.php?t=1617&highlight=linux)

tell me if anyone got it to play under Linux.
and enjoy !

**_P.S_**
the default client is **NOT** in English
BUT there is an option in "options" to make it in English.
you have to mess with them.

---

### Post by finferflu on 2006-12-01
Haven't tried it yet, but it looks promising. I also like the philosophy behind it, and hope they keep their promise.

Thanks for sharing!

---

### Post by haxer on 2006-12-01
Really nice game im already an warrior level 4 :) i think its nice looks good and lots of fun and simple quests the only thing thats bad is that there is to much spanish people i cant understand nothing :( ;)

---

### Post by Malikith on 2006-12-01
This looks really interesting, i'll check it out, i'm not much of a mmorpg player (I'm a FPS guy) but this looks like it has some good quality to it. Looks like its worth checking out to me by the screenshots and the fact its got a native linux client. Heres the link to the "Unofficial Linux Client" so no one has to dig through that site:

[http://www.regnumonline.com.ar/forum/showthread.php?t=1617&highlight=linux](http://www.regnumonline.com.ar/forum/showthread.php?t=1617&highlight=linux)

---

### Post by MonkeyBoy on 2006-12-01
That how to worked pretty well but I can't get sound to run in the game.  Any of you have similar problems?  

By the way I picked Ignis and am called Flames so say "hi" if you see me around!  :)

---

### Post by Malikith on 2006-12-01
> **MonkeyBoy said:**
> That how to worked pretty well but I can't get sound to run in the game.  Any of you have similar problems?  

By the way I picked Ignis and am called Flames so say "hi" if you see me around!  :)

Well I run 64-bit Ubuntu and getting sound in game was a pain, I had to quite a few libraries by hand, by extracting deb packages from the Ubuntu repository for 32-bit and placing all the files I needed in the /usr/lib32 directory. Its a pain, to find out what ones you'll need you gotta look quick at the command console that pops up for about a split second and you'll see it fails to find openal in red text, then around it you'll see the file it couldn't find. I hope they make it easier in the future.

The game is probably the highest quality mmorpg i've played in native linux however. But it needs a bigger English speaking user base and some more translation done to some of the in game text, but it still is in beta and is worth keeping an eye on.

---

### Post by MaximB on 2006-12-02
I'm afraid to say but this game is more playable then planeshift at this stage for me.
and I always supported planeshift.

---

### Post by fng on 2006-12-02
> **MonkeyBoy said:**
> That how to worked pretty well but I can't get sound to run in the game.  Any of you have similar problems?

I also have no sound in the game.

---

### Post by haxer on 2006-12-02
Me to idont think there should be sound i have music from xmms and streamtuner instead much cooler :)

---

### Post by MonkeyBoy on 2006-12-02
Well I checked the console like Malikith suggested and it seems to fail finding libopenal.so.  I have looked about for this but it isn't in my repos.  

As a bit of a n00b in these matters I would very much appreciate any suggestions regarding getting the sound running on 32bit Dapper.

---

### Post by drphilngood on 2006-12-02
Great find; thanks.

---

### Post by Shatrat on 2006-12-02
If you have no sound it's probably because its probably not finding your openal library.  I did the following and it worked (32 bit edgy).
```
sudo ln -s /usr/lib/libopenal.so.0.0.0 /usr/lib/libopenal.so
```
Basically the game looks for libopenal.so when it needs libopenal.so.0.0.0

---

### Post by Malikith on 2006-12-02
> **MonkeyBoy said:**
> That how to worked pretty well but I can't get sound to run in the game.  Any of you have similar problems?  

By the way I picked Ignis and am called Flames so say "hi" if you see me around!  :)

Hey I saw you said hi to me in game wondering if I was the same Malikith, I was ;), I was afk though.

---

### Post by MonkeyBoy on 2006-12-03
Cool!  It's a small world!
See you around.

---

### Post by msak007 on 2006-12-03
I just recently discovered this game through another post in the forum, and it looks great. I registered and I'm just about to try it out. I got the Linux client and installed it using [this]("http://www.regnumonline.com.ar/forum/showthread.php?t=1617&highlight=linux") post in their forums, found my way around the menus and changed it to English, and launched it. Great but, just like the others, no sound. Then I stumbled on [this]("http://www.regnumonline.com.ar/forum/showthread.php?t=1063") thread, also in their forums, that discusses the sound issues. I installed **libopenal0a** (and installed the corresponding dev package as suggested just in case) and then launched the game, and got partial sound but it still sounded weird. So I followed that last post and created the .openalrc file and it seems to have fixed the issue.

EDIT: What Realm are you guys on? I'd like to at least play online with familiar users and preferably someone who speaks English :).

---

### Post by MonkeyBoy on 2006-12-04
That sound fix works fine for me too.  Thanks for the link.  

I think there are only 2 servers and I am on the normal one (not the experimental one) in Ignis.  See you there!

---

### Post by willneedshelp... on 2006-12-05
when i start the game it goes in and out of picture sometimes i can see the first screen of the game but then it goes white i get this message...

fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!

anyone have a clue as to what im to do about this

---

### Post by Shatrat on 2006-12-05
You should go into the options on the launcher and set it to use OpenGL rendering.
I don't know why it is trying to use d3d for you, it doesn't even give me the option.

edit:
Wait, are you trying to run the windows client in wine?  The whole point of this post is the fact that there is a native linux client.

---

### Post by willneedshelp... on 2006-12-05
ok got the game working but i have sound issue im a little confused on what to do there anyone clarify for me please?

---

### Post by qrm on 2006-12-05
just check previous posts in this thread, itll help you out

---

### Post by haxer on 2006-12-05
The game stinks ... im keep getting kicked from the game ,. ... no admin isnt kicking me. 
Sudenly when im playing the game turns off? 
BTW its really slow leveling i played it for like 5 days and im still level 12 ;)

---

### Post by MaximB on 2006-12-06
after todays update I can't connect to the server
anyone managed to connect today ?

---

### Post by willneedshelp... on 2006-12-07
yea i figured it out and got everything working fine but when i played today and i couldnt do any quests...it froze on me...did any of u witness this too?:confused:

---

### Post by MaximB on 2006-12-07
actually when I played today in winxp (due to the Linux client crash on my machine) the game always crashed when I tried to do ANY quests.
so it's a problem in the game.

---

### Post by willneedshelp... on 2006-12-07
i was playing with some people and someone did the nash quest today but i froze someone else said it happned to them too so it cant be all....i wounder:confused:

---

### Post by MaximB on 2006-12-07
tell me please , how did you fix the Linux client problem ?
it was fine before , but no after I choose my character and click play
the resources starts to load and then after 1 minute it quits.
I installed it again and downloaded all resources first and still the same problem.
in winxp it works fine (except the quests part) :(

I got this crash backreport :

```

libs/libcore_client.so(_ZN10ClientBase14save_backtraceEv+0x7e) [0xb7d2862e]
libs/libcore_client.so(_ZN10ClientBase12client_crashEi+0x17) [0xb7d28937]
[0xffffe420]
/lib/tls/i686/cmov/libc.so.6(backtrace_symbols+0x82) [0xb70f9722]
libs/libcore_client.so(_ZN10ClientBase14save_backtraceEv+0x96) [0xb7d28646]
libs/libcore_client.so(_ZN10ClientBase12client_crashEi+0x17) [0xb7d28937]
[0xffffe420]
libs/libos.so(pool_malloc+0x32) [0xb73fedc2]
libs/libos.so(_ZN19pool_allocator_base5allocEjPv+0x33) [0xb73fdb43]
libs/libmisc.so(_ZNSbIcSt11char_traitsIcE14pool_allocatorIcEE4_Rep9_S_createEjjRKS2_+0x94) [0xb74250e4]
libs/libmisc.so(_ZNSbIcSt11char_traitsIcE14pool_allocatorIcEE4_Rep8_M_cloneERKS2_j+0x40) [0xb7425330]
/usr/lib/dri/fglrx_dri.so(_ZNSbIcSt11char_traitsIcE14pool_allocatorIcEE7reserveEj+0x57) [0xb667ed17]
/usr/lib/dri/fglrx_dri.so(_ZNSbIcSt11char_traitsIcE14pool_allocatorIcEE6appendEjc+0x5f) [0xb667d89f]
/usr/lib/dri/fglrx_dri.so(_Z21InitStandardFunctionsR12TSymbolTable+0x1f3) [0xb669c623]
/usr/lib/dri/fglrx_dri.so(ShCompile+0x7a5) [0xb667af55]
/usr/lib/dri/fglrx_dri.so(__glslATICompileVertexShader+0x86) [0xb61f1ee6]
/usr/lib/dri/fglrx_dri.so(__glim_CompileShaderARB+0x176) [0xb627c146]
libs/libopengl_api.so(_ZN8Engine3D8ShaderGL13define_shaderEjPKcS2_b+0x634) [0xb76a7ce4]
libs/libopengl_api.so(_ZN8Engine3D8ShaderGL9configureERK17DynamicDataStruct+0x1560) [0xb76ae710]
libs/libopengl_api.so(_ZN8Engine3D8GLParser14load_gl_shaderERSt6vectorIhSaIhEEPNS_8ShaderGLE+0xcb) [0xb76c2e7b]
libs/libopengl_api.so(_ZN8Engine3D8GLParser14load_gl_shaderEPKcPNS_8ShaderGLE+0x1e9) [0xb76c3259]
libs/libopengl_api.so(_ZN8Engine3D8ShaderGL6createESsb+0xd4) [0xb76a2b84]
libs/libresource_system_extension.so(_ZN12ShaderSystem8CManager10get_shaderERKSs+0x283) [0xb7780b03]
libs/libresource_system_extension.so(_ZN12ShaderSystem8CManager24resource_loaded_callbackEP7Message+0x5f0) [0xb7782470]
libs/libentity_system.so(_ZN6Entity22input_message_internalEP7Message+0x175) [0xb7538fa5]
libs/libentity_system.so(_ZN6Entity13input_messageEP7Message+0x20) [0xb7537390]
libs/libentity_system.so(_ZN18EntityMessageQueue17process_a_messageEv+0x314) [0xb7518174]
libs/libentity_system.so(_ZN18EntityMessageQueue16process_messagesEv+0x9f) [0xb751939f]
libs/libentity_system.so(_ZN12EntitySystem10poll_frameEv+0x33) [0xb7512c73]
libs/libcore_client.so(_ZN10ClientBase7iterateEv+0x49) [0xb7d28739]
libs/libregnum_client.so(_ZN10GameClient7iterateEv+0x2c) [0xb7edc65c]
libs/libcore_client.so(_ZN8MainLoop7iterateEv+0x28) [0xb7d3a118]
./game(main+0x47) [0x8048b77]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb702e8cc]
./game(__gxx_personality_v0+0x61) [0x8048a91]
```

help please.

---

### Post by willneedshelp... on 2006-12-07
i got the same crash backtrace with my linux when i try to do quests...it lets me do some but not very many like 1 out of 5](*,)

---

### Post by Josey on 2006-12-08
This game rocks!  Make sure to grab openAL from the repositories for the sount ot work.

---

### Post by willneedshelp... on 2006-12-09
hell yea this game rocks im like a 15 barbarian if any of u see metlgear say hi thats me i will play with you...LINUX PLAYERS UNITE!

---

### Post by Josey on 2006-12-09
The pvp in this game is excellent.  Try this one if your looking for a good mmorpg.

---

### Post by MaximB on 2006-12-10
I'm making an English speaking clan in Alsius.
so if you level 15+ (game rules) please post here :
[http://www.regnumonline.com.ar/forum/showthread.php?t=1912](http://www.regnumonline.com.ar/forum/showthread.php?t=1912)

thanks.

---

### Post by JMO707 on 2006-12-11
Can anyone with a forum account report the quests issue to the developers?

I cant register and is a real shame than that little-big thing doesnt work :(

---

### Post by msak007 on 2006-12-12
My initial impression of the game wasn't that great after playing it for an hour or so, but after playing it again yesterday I got a little more into it. Some little quirks I'm still not used to (compared to other games I've played):

1. Being able to rotate the camera while running with the WASD keys. What I mean is when rotating the camera via holding down the right-click, instead of changing directions the character keeps running in the direction the key is dictating. If I'm holding W (to run straight) and rotate the camera to the right while holding down the key, my character continues to run "straight" even though it looks like he's running left. Any other MMORPG I've played switches the direction your character is running depending on the camera view, so you're always running straight. *TIP* I've found that right-clicking anywhere when you're not moving, or left-clicking on the compass, will center your camera again.

2. Having to be within range to attack or speak. If I double-click on a character, I expect my character to run to the character I want to interact with. Instead it tells me I'm too far away. I experience the same behavior when attacking - rather than move the character within range, it just complains I'm too far away.

3. Last but not least - the constant crashing. I know that the Linux client is not officially supported, but it just crashes way too often. It just crashed on me yesterday and I lost a weapon as a result.

And yes it is quite annoying that it crashes when you attempt to request a quest from any NPC. I'm basically stuck right now without any quests to do. 

**MAXDDARK** - I'm in Alsius, but I'm currently only a level 4. I'll let you know when I reach 15. BTW I'm not registered on those forums, but I have a clan name suggestion: A.K.A (Alsius Kicks @$$ :)).

---

### Post by RomeReactor on 2006-12-12
> **Josey said:**
> The pvp in this game is excellent.  Try this one if your looking for a good mmorpg.

I agree. Too bad about the quest bugs, but since it's still beta i'll keep playing and wait for the fix. I really liked this game, even though I'm not much into the mmorpg genre.

> **willneedshelp... said:**
> hell yea this game rocks im like a 15 barbarian if any of u see metlgear say hi thats me i will play with you...LINUX PLAYERS UNITE!

hi metlgear! I'm Moonshadow in Ignis. See you around:mrgreen:

PS: My very first post, yay!!

---

### Post by JMO707 on 2006-12-12
They solved the quest bug!!! =D

---

### Post by TheTank on 2006-12-13
I signed up but have not yet recieved a confirmation mail.
I have tried sending an email to the email address noted on the post-signup-screen but got an failure notice from the mail demon.

I look forward to meeting some of you online.

---

### Post by hikaricore on 2006-12-23
Msak007, thank you for the sound fix link, I finally got a chance to install this and play it on my system.  :)  It's not bad, and like some of you I'm used to the controls of other games, perhaps they will get better overtime.  It could also do with customized keybindings... and for the love of all that is unholy and bad, A WAY TO SKIP ATLEAST THE STORY INTRO...sorry bout that, I'm tired of her voice already.

Anyway, I wanted to present you all with a screenshot of me exploiting game physics (yes this one is lame and didn't take more than 5 minutes):
[B]
I [COLOR=Red]<3[/COLOR] Wall-Walking[/B]
[IMG]http://img.photobucket.com/albums/v414/hikari_corgan/junk/screenshot2006-12-2302_40_54.jpg[/IMG]

I'll be finding much more difficult places to get to eventually and post more screenshots of me standing in said hard to get places.

---

### Post by Lord Illidan on 2006-12-23
I tried the game, solved the sound problem.

However, I really wish for 2 things.

1. More English players..I cannot understand spanish v. well
2. More english translators..certain quests and the help app are all spanish

How do I get past the Wasps quest? I cannot read the quest (spanish) and where are the wasps?

---

### Post by haxer on 2006-12-23
I must agrey with lord here ... why not make english and spanish so spanish people can chat in spanish and english chat in english and all quest "almost" in spanish wtf is that? English is an global language why not use it? :-k

---

### Post by msak007 on 2006-12-23
> **hikaricore said:**
> Msak007, thank you for the sound fix link, I finally got a chance to install this and play it on my system.  :)  ... and for the love of all that is unholy and bad, A WAY TO SKIP ATLEAST THE STORY INTRO...sorry bout that, I'm tired of her voice already.
You're welcome. Regarding the horrid intro, ESC does the trick :). But yea there should be an option to completely disable it at startup once you've seen it.

I agree with the others about the whole English / Spanish thing, I've gotten pretty good at saying "Lo siento, no hablo ingles" lol. There should be some sort of option in your preference to specify if you're an English or Spanish speaker, and the game should filter other players currently online accordingly (if you desire it) so only Spanish or English players are visible to you. Nothing against Spanish players, but there's no point in me conversing or grouping with someone I can't understand. 

Seriously though it is free and the developers are in Argentina, so you can't expect everyone working on this game to be fully fluent in English and everything to be 100% translated. Let's not be so narrow minded (no offense intended) and expect everyone to speak perfect English (they don't expect us to speak Spanish). If some players are fluent in both English and Spanish I'm sure they could offer the help to translate menus, quest dialogs, chat dialogs, etc. and help the developers out. Unfortunately I don't qualify for that. I simply use the bug report tool whenever I find something that's not translated, or if it is poorly translated and has some spelling or grammar mistakes (I'm a spelling / grammar Nazi lol). You guys should do the same if you want to help the game out.

---

### Post by RomeReactor on 2006-12-23
> **hikaricore said:**
> ...I'll be finding much more difficult places to get to eventually and post more screenshots of me standing in said hard to get places.

For hard to reach places try the following coordinates: 5641 1655
Or these: 6036 1452
Those are the highest places i've been in Ignis, let's see if someone can top that:mrgreen: 

> **msak007 said:**
> You're welcome. Regarding the horrid intro, ESC does the trick :). But yea there should be an option to completely disable it at startup once you've seen it.

I agree with the others about the whole English / Spanish thing, I've gotten pretty good at saying "Lo siento, no hablo ingles" lol. There should be some sort of option in your preference to specify if you're an English or Spanish speaker, and the game should filter other players currently online accordingly (if you desire it) so only Spanish or English players are visible to you. Nothing against Spanish players, but there's no point in me conversing or grouping with someone I can't understand. 

Seriously though it is free and the developers are in Argentina, so you can't expect everyone working on this game to be fully fluent in English and everything to be 100% translated. Let's not be so narrow minded (no offense intended) and expect everyone to speak perfect English (they don't expect us to speak Spanish). If some players are fluent in both English and Spanish I'm sure they could offer the help to translate menus, quest dialogs, chat dialogs, etc. and help the developers out. Unfortunately I don't qualify for that. I simply use the bug report tool whenever I find something that's not translated, or if it is poorly translated and has some spelling or grammar mistakes (I'm a spelling / grammar Nazi lol). You guys should do the same if you want to help the game out.

Wow, i was about to say practically those same words. Coincidence? I think not.... errr, well, maybe8)

---

### Post by mongrol on 2006-12-24
> **TheTank said:**
> I signed up but have not yet recieved a confirmation mail.
I have tried sending an email to the email address noted on the post-signup-screen but got an failure notice from the mail demon.

I look forward to meeting some of you online.

Same here. Signed up last week. Tried the "resend" activation email function on the support page. No email, no regnum for me, no luck.

---

### Post by msak007 on 2006-12-24
Not sure if they're having problems with sign-ups, but if you used a free web-based mail service are you guys sure you checked your Junk folders? I had the email sent to my Hotmail account and it went straight to the Junk folder. You can try [this]("http://www.regnumonline.com.ar/index.php?l=1&sec=20&subsec=1") page to resend the activation email again (if you haven't done so) and see if it shows up. This is from the bottom of the page:

> If the problem persists, try using another e-mail address. Several users from Hotmail Msn, Yahoo, Gmail are already playing the game.
So if all else fails, try another email address.

---

### Post by MaximB on 2006-12-24
I've been playing in Alsius but almost all quests and game aspects are in English (yeah they have grammar mistakes "he/she" but it's understandable).
now I'm level 24 and I paused playing due to real life and no quests in 20-32 levels :( (at the moment, this will change).

---

### Post by mongrol on 2006-12-24
> **msak007 said:**
> Not sure if they're having problems with sign-ups, but if you used a free web-based mail service are you guys sure you checked your Junk folders? I had the email sent to my Hotmail account and it went straight to the Junk folder. You can try [this]("http://www.regnumonline.com.ar/index.php?l=1&sec=20&subsec=1") page to resend the activation email again (if you haven't done so) and see if it shows up. This is from the bottom of the page:

So if all else fails, try another email address.

Sussed. My email address had a 2 char mailbox. I've had this before with other sites. Changed email addy and it came through straight away.

---

### Post by RomeReactor on 2006-12-24
Don't know if this is news, but after being down for most of the day the server is now back online...:cool:

---

### Post by Josey on 2006-12-25
dam does anyone know where to get good bows in the warzone for ignis?

---

### Post by redbluemangle on 2006-12-25
I'm going to try this game out. Hopefully the fact that I STILL cant get my ATi card working really wont matter. maybe the original poster would like to link to the english site? [http://www.regnumonline.com.ar/eng_site/](http://www.regnumonline.com.ar/eng_site/)

---

### Post by EdThaSlayer on 2007-01-03
This game rocks! I hope that the weird sound issue got fixed by the terminal commands "someone"[forgot the name...] made for us. Iam in Ignus too[I hope that is the evil red flagged- dark elf area]. The client does crash for me, only after 10-20 minutes of playing though.

---

### Post by SBFC on 2007-01-04
So...am I totally blind or is there no buddy list in Regnum?

---

### Post by EdThaSlayer on 2007-01-04
> **SBFC said:**
> So...am I totally blind or is there no buddy list in Regnum?

Well,I think you can make friends...
I never thought about this:-k 
Let me check...


EDIT: There is no such thing as a buddy list in this game.

---

### Post by dtruesdale on 2007-01-04
The client still has some gliches but overall it's free, and still in Beta.

---

### Post by aktiwers on 2007-01-09
Someone should make a howto for this game.. 
When I hit the play button after I logged in, it just quits the game :(

---

### Post by Kubunteando on 2007-01-12
Same here. Just it gives a crash report.
It seems there are issues with 6.10 edgy, and it is working better with 6.0.6 dapper.

I hope they are fixing things soon... I really would like to try the game.

---

### Post by Extreme Coder on 2007-01-12
Same here, when I click play, the resolution gets very small, and the game quits :(

---

### Post by MaximB on 2007-01-13
in "my" edgy it's working great.
but if you have a problem you SHOULD post in regnum forum , there is only one Linux programmer there and you should let him know about the problems so he could fix them
the developers are actually very active in those forums, so you should post there (I did it at the time and they fixed "my" problem).

---

### Post by RomeReactor on 2007-01-14
@ Kubunteando & Extreme Coder: I'm running edgy, and aside from the sound issue (which i solved with [this]("http://www.regnumonline.com.ar/forum/showthread.php?t=2143") thread), it has always run perfectly on my system. What exactly is the problem that's afflicting your respective PC's?

---

### Post by msak007 on 2007-01-14
If your Regnum is crashing when you first click "Play" - are you guys using a laptop with an ATI card in conjunction with the open source ati / radeon driver?

---

### Post by alecto on 2007-01-14
I am using ATI 7500 mobility in an IBM T40. I'm using the DRI Open Source Drivers and when I hit play the game simply doesn't load](*,) .

Would love to have a decent MMORPG to play, If you have any ideas i'd love to hear them!

---

### Post by msak007 on 2007-01-14
> **alecto said:**
> I am using ATI 7500 mobility in an IBM T40. I'm using the DRI Open Source Drivers and when I hit play the game simply doesn't load](*,) .

Would love to have a decent MMORPG to play, If you have any ideas i'd love to hear them!
That's the problem then. The open source drivers can't legally include or support the S3TC compression that is needed because S3 still owns the patent and all related IP. The proprietary drivers from ATI include it, but your card isn't supported by the driver. I have the same problem with my laptop, which uses a Radeon Mobility M6 LY. The game requires S3TC, so that's why it crashes when you first launch it. [Here']("http://dri.freedesktop.org/wiki/S3TC?action=highlight&value=s3tc")s the explanation from the DRI page. There are several guides out there on how to build the driver with S3TC compression included, but they're all severely outdated and I haven't found any step by step instructions to do it.

---

### Post by alecto on 2007-01-14
> **msak007 said:**
> That's the problem then. The open source drivers can't legally include or support the S3TC compression that is needed because S3 still owns the patent and all related IP. The proprietary drivers from ATI include it, but your card isn't supported by the driver. I have the same problem with my laptop, which uses a Radeon Mobility M6 LY. The game requires S3TC, so that's why it crashes when you first launch it. [Here']("http://dri.freedesktop.org/wiki/S3TC?action=highlight&value=s3tc")s the explanation from the DRI page. There are several guides out there on how to build the driver with S3TC compression included, but they're all severely outdated and I haven't found any step by step instructions to do it.

I had a quick search on google and it seems that you can simply fire up 'driconf' in a terminal and enable S3TC support from there. In the Image Quality tab I ticked the "Enable S3TC..." box and changed it to 'Yes' and now the game loads!

However!... Upon successfully loading I get an error message saying it couldn't connect to the server. I assume this is to do with my connection being blocked by my university or perhaps the server's down.

Hope it helps someone anyway.

---

### Post by msak007 on 2007-01-14
> **alecto said:**
> I had a quick search on google and it seems that you can simply fire up 'driconf' in a terminal and enable S3TC support from there. In the Image Quality tab I ticked the "Enable S3TC..." box and changed it to 'Yes' and now the game loads!
I wasn't aware of driconf. I didn't see any mention of S3TC being a requirement anywhere on the game's site, and no instructions in the forums on how to turn it on. Thanks for the tip, I'll have to give it a try on my laptop. It's only 8 MB so the game won't be playable, but I'll test it to see if it works.

---

### Post by RomeReactor on 2007-01-15
Hi. For anyone that's annoyed by Regnum dumping all those files on your home folder, i figured out a solution (i'm posting it here because i haven't seen it anywhere else; i also posted it on the [Regnum Forums]("http://www.regnumonline.com.ar/forum/showthread.php?t=2656"):

I installed Regnum on "/home/sho/.games/regnum"; however, the game kept making the files on "/home/sho". To solve that annoying issue with regnum dumping all files on your home folder, create a launcher by right-clicking on your desktop and selecting "Create Launcher" (or modify the one you already have) and fill the "Command:" section thus:

```
sh -c "cd /home/sho/.games/regnum && ./rolauncher"
```

Remember to change the directories according to your own. Now move all the game's files (including the "live" and "test" folders) to your regnum directory and run the launcher.

---

### Post by aktiwers on 2007-01-15
Yeah I have an ATI 9200SE :(
Anyways, I downloaded the driconf via synaptic and fired it up..

I added the stuff mentioned above and my FPS in glxgears went up with almost 10 times!! :)

I fired up regnum and this time it takes me to the terminal window after I hit play, but a little down it gives me the " cant open OpenAL" Error?
Then it takes me to a screen with ATI and Nvidia Logos, and shutsdown..

Any idea's ?? Heres a screeenshot:

---

### Post by aktiwers on 2007-01-15
I just installed OpenAL, and now that error is gone.
However, the game still closes/crashes after the screen with ATI and Nvidia logos.. :(

Any suggestions?

---

### Post by RomeReactor on 2007-01-16
What's the output it gives you from running it in a terminal?

---

### Post by aktiwers on 2007-01-17
This is all it gives me

```
Saving backtrace to crash_backtrace_8504.log
Got SIGSEGV (segmentation fault)
```

Where can I find that log? Anyone knows how to fix it!
I so badly wanna try this game! :)

---

### Post by RomeReactor on 2007-01-17
Inside your Regnum folder are two more: "live" and "test" (at least "live" should be, i think). The backtrace should be inside "live". If Regnum is dumping it's files on your home directory, look for the folder there.

---

### Post by aktiwers on 2007-01-17
This is what the log says:
```
libs/libcore_client.so(_ZN10ClientBase14save_backtraceEv+0x7e) [0xb7de054e]
libs/libcore_client.so(_ZN10ClientBase12client_crashEi+0x17) [0xb7de0857]
[0xffffe420]
/usr/lib/dri/r200_dri.so [0xb6875acd]
/usr/lib/dri/r200_dri.so [0xb687166d]
/usr/lib/dri/r200_dri.so [0xb6873100]
/usr/lib/dri/r200_dri.so [0xb6842d93]
/usr/lib/dri/r200_dri.so(_ae_loopback_array_elt+0x329) [0xb67cc0b9]
/usr/lib/dri/r200_dri.so [0xb69142b8]
/usr/lib/dri/r200_dri.so(_tnl_DrawArrays+0x124) [0xb6914614]
/usr/lib/libGL.so.1(glDrawArrays+0x38) [0xb6f6daa8]
libs/libopengl_api.so(_ZN8Engine3D12RenderizerGL22render_surface_elementEPNS_10RenderList14SurfaceElementEPNS_25ObjectRenderingParametersE+0xe51) [0xb77b0331]
libs/libopengl_api.so(_ZN8Engine3D12RenderizerGL11render_meshEPNS_4MeshEP8Matrix4D+0xd9) [0xb778d5f9]
libs/libopengl_api.so(_ZN8Engine3D12RenderizerGL15render_gui_meshEffPNS_4MeshEPKSt6vectorI10BitmapBaseSaIS4_EEPKS3_I13StringElementSaIS9_EEf+0xfd) [0xb778d78d]
libs/libgui_extension.so(_ZN3GUI16Drawable_GUIMesh15render_internalEv+0xd9) [0xb798eb09]
libs/libgui.so(_ZN3GUI8Drawable6renderEv+0x36) [0xb7a6efa6]
libs/libgui.so(_ZN3GUI6Widget11draw_signalENS_9AreaCoordE+0x197) [0xb7a43da7]
libs/libgui.so(_ZN3GUI6Widget11draw_signalENS_9AreaCoordE+0x1dd) [0xb7a43ded]
libs/libgui.so(_ZN3GUI6Widget11draw_signalEv+0x83) [0xb7a440d3]
libs/libcommon_entities.so(_ZN13DisplayEntity15show_next_frameEv+0x3d) [0xb7c1efad]
libs/libregnum_client.so(_ZN10GameClient7iterateEv+0x42) [0xb7f70ff2]
libs/libcore_client.so(_ZN8MainLoop7iterateEv+0x28) [0xb7df0568]
./game(main+0x47) [0x8048b67]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb70f38cc]
./game(__gxx_personality_v0+0x61) [0x8048a81]
```

Any ideas?

---

### Post by RomeReactor on 2007-01-17
Are you using the ati open source drivers? If so, did you try driconf, as suggested by alecto a few posts above?

---

### Post by aktiwers on 2007-01-18
Yes, I did try driconf, and that gave me almost 10 times higher FPS.
Also before I did driconf, the game would close when I hit the play button, not even showing me the loading and the ATI & Nvidia screen.

Thanks though..  Any other idea's suggestions? :)

---

### Post by Extreme Coder on 2007-01-18
Following your advice, I tried out the FGLRX drivers. And guess what? The game worked! It's working very smoothly now, but I don't know why the sound is VERY scratchy all the time :(

Thanks!

Extreme Coder

---

### Post by hikaricore on 2007-01-18
> **Extreme Coder said:**
> Following your advice, I tried out the FGLRX drivers. And guess what? The game worked! It's working very smoothly now, but I don't know why the sound is VERY scratchy all the time :(

Thanks!

Extreme Coder

Open a terminal, you should be in your home directory.  Type:

```
gedit .openalrc
```

And paste the following:

```
(define devices '(native))
```

Save the file, exit gedit and start the game.  Your sound issues should be resolved.

---

### Post by K.Mandla on 2007-01-18
I had to install [libopenal0a]("http://packages.ubuntu.com/edgy/libs/libopenal0a") too, but after that the .openalrc trick worked for me.

---

### Post by aktiwers on 2007-01-18
No ideas for me?? :(

---

### Post by RomeReactor on 2007-01-18
Have you tried running it in 16-bit color?

---

### Post by aktiwers on 2007-01-18
yep - it is already in 16 bit when I get these errors.

---

### Post by RomeReactor on 2007-01-18
As a last resort, try installing ATI's proprietary drivers... :neutral:

---

### Post by patrick295767 on 2007-01-19
Thank you max for always your great findings for LInux & MMORPH online !

---

### Post by patrick295767 on 2007-01-19
Great game but I banned  this game for the moment:
due to minor **security hole**
ps ax 
gives you the pasword.
  
Can someone report them ? I feel lazy of it..

---

### Post by aktiwers on 2007-01-20
I have an ATI 9200SE which is not supported by ATI anymore. I tried to install the old drivers from ATI that do support my card, but without any luck..

Is this really the last resort? :(

Else I will probably have to wait with this game, until I can afford a new computer (years!)..

Thanks a lot for the help anyways :)

---

### Post by RomeReactor on 2007-01-20
Are you using the xorg-driver-fglrx driver that is in Synaptic? Have you looked [here]("http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html") (the 9200 series drivers page) for the drivers from ATI?

EDIT: As suggested [here]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Disable_Composite_Extension"), if you're using fglrx, Edgy doesn't support the composite extension with dri; so:

```
sudo gedit /etc/X11/xorg.conf
```

and

```
Section "Extensions"
        Option  "Composite" "Disable"
EndSection
```

ANOTHER EDIT: [These]("http://www.ubuntuforums.org/showthread.php?t=221320") [threads]("http://www.ubuntuforums.org/showthread.php?t=340758") might help you. Don't give up!

---

### Post by MaximB on 2007-01-21
> **patrick295767 said:**
> Thank you max for always your great findings for LInux & MMORPH online !

actually I've found this game via [www.mmorpg.com](www.mmorpg.com) , I've searched for some free Linux clients and luckily I've found this game. (had to search 100 mmorpg's to find this one ;).
but you found a very addictive game yourself
[www.knightfight.co.uk](www.knightfight.co.uk) - now I'm hooked ! I can't stop playing it daily.
(at this point they kick my *** but this will change soon, I hope ;)).

P.S
you should use your messenger more, I haven't seen you for months !

---

### Post by jpeirce on 2007-01-23
I'm having trouble starting the game as well.  When I press play it quickly shows the window it would be loaded in, then crashes  to the terminal, with Output: 

libGL warning: 3D driver claims to not support visual 0x5b

I've tried enabling S3TC Texture compression, but that doesn't really help.

My graphics card is an Intel i915, with DRI enabled. 

This is the contents of log.txt:

[RenderizerGL][renderizer_gl_x11.cpp(158)] X Server vendor: The X.Org Foundation
[RenderizerGL][renderizer_gl_x11.cpp(162)] X Server release: 7.1.1
[RenderizerGL][renderizer_gl.cpp(388)] Got a 24 bit visual with a 24 bit depth buffer
[RenderizerGL][renderizer_gl.cpp(408)] OpenGL vendor: Tungsten Graphics, Inc
[RenderizerGL][renderizer_gl.cpp(409)] OpenGL renderer: Mesa DRI Intel(R) 915GM 20050225
[RenderizerGL][renderizer_gl.cpp(410)] OpenGL version: 1.3 Mesa 6.5.1
[RenderizerGL][renderizer_gl_extensions_loader.cpp(202)] Detected OpenGL extensions: GL_ARB_fragment_program, GL_ARB_imaging$
[EventImportBase][event_import_base.cpp(80)] Toplevel widget not assigned
[EventImportBase][event_import_base.cpp(80)] Toplevel widget not assigned
[EventImportBase][event_import_base.cpp(80)] Toplevel widget not assigned
[EventImportBase][event_import_base.cpp(80)] Toplevel widget not assigned
[EventImportBase][event_import_base.cpp(80)] Toplevel widget not assigned
[EventImportBase][event_import_base.cpp(80)] Toplevel widget not assigned
[EntitySystem][entity_system.cpp(95)] Entity system ready to shutdown
[Game][game_client.cpp(641)] Exiting Game

---

### Post by Kubunteando on 2007-01-26
It seems that the MESA DRI drivers are not supported at the moment.

You can check the Linux forums on the official site.
I made a request there so the support to the Open Source drivers is added, but I guess the chances are realy small.

So you need and NVIDIA or ATI card with fglrx drivers.
Also it seems that there are problems with edgy even with fglrx drivers...

---

### Post by Frazer on 2007-02-03
I just got the game installed, first impressions are very good :) especially for a Beta

I still havent got sound and get a lot of crashes trying to run the game, but once its running it seems fine :)

---

### Post by aktiwers on 2007-02-04
Oh yeah..   Im buying a nVidia soon, so I dont bother trying anymore.. thanks for all the help guys :)

---

### Post by aktiwers on 2007-02-07
Got my nVidia, plugged it in.. installed it and Im now playing Regnum!!
Thanks for the support guys..  

Im lvl 10, playing on Ignis!

---

### Post by zeroblitzt on 2007-02-07
Just started today, great game. Level 4 on Ignis.

---

### Post by RomeReactor on 2007-02-08
Hi guys. Though i don't play as often as i used to, i'm also on ignis; look for Moonshadow and say hi! ):P

---

### Post by Megatog615 on 2007-02-10
Why can't I see the mouse cursor?

---

### Post by tallrichie on 2007-02-10
*[FONT="Trebuchet MS"]a pretty good game even its in beta. At least they are going to do a  free2play kind when it goes to retail that the basic game will be free and you have to pay for the premium content and they are making sure the premium doesn't unbalanced the game which is nice.[/FONT]*

---

### Post by veelos on 2007-04-20
Hi, I installed this game and also the libs needed by it, but I can't get past the realm screen.. I also installed the driconf, but there is no box to tick to get this S3TC thing working. It crashes to the part where it says "Loading Realm Data". And yes, I have fglrx drivers. Here's my crashlog:

```

libs/libcore_client.so(_ZN10ClientBase14save_backtraceEv+0x7e) [0xb7e07cfe]
libs/libcore_client.so(_ZN10ClientBase12client_crashEi+0x17) [0xb7e080a7]
[0xffffe420]
/usr/lib/dri/fglrx_dri.so [0xb68325dc]
/usr/lib/dri/fglrx_dri.so [0xb67c49ac]
/usr/lib/dri/fglrx_dri.so(__glim_TexImage2D+0x9d) [0xb67cc74d]
libs/libopengl_api.so(_ZN8Engine3D12RenderizerGL17gl_upload_textureEP7TexturePNS_10GL_TextureEi+0x688) [0xb777d998]
libs/libopengl_api.so(_ZN8Engine3D12RenderizerGL14update_textureEiP7Texture+0x660) [0xb777f4b0]
libs/libresource_system_extension.so(_ZN14TextureManager24process_texture_resourceEP15ResourceTexture+0xf8) [0xb7818748]
libs/libresource_system_extension.so(_ZN14TextureManager15resource_loadedEP7Message+0x2c9) [0xb7819f49]
libs/libentity_system.so(_ZN6Entity22input_message_internalEP7Message+0xc8f) [0xb75dca1f]
libs/libentity_system.so(_ZN6Entity13input_messageEP7Message+0x22) [0xb75dac12]
libs/libentity_system.so(_ZN18EntityMessageQueue17process_a_messageEP7Message+0x2a2) [0xb75ba9a2]
libs/libentity_system.so(_ZN18EntityMessageQueue16process_messagesEv+0xf9) [0xb75bbc79]
libs/libentity_system.so(_ZN12EntitySystem10poll_frameEv+0x39) [0xb75b57f9]
libs/libcore_client.so(_ZN10ClientBase7iterateEv+0x4f) [0xb7e07e8f]
libs/libregnum_client.so(_ZN10GameClient7iterateEv+0x2c) [0xb7f99a0c]
libs/libcore_client.so(_ZN8MainLoop7iterateEv+0x28) [0xb7e16e78]
./game(main+0x47) [0x8048b67]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb709debc]
./game(__gxx_personality_v0+0x61) [0x8048a81]

```

I also get this error message before the game launches: 
Error uploading texture : Invalid operation

And I have 3D acceleration working.

---

### Post by Kubunteando on 2007-05-05
Some hope here for the folks using the Mesa Open Source Drivers.
Last month it was released the Mesa version 6.5.3, I have tried it and I can start the game!
Before I was being kick out before loading the resources.
I have played much but this is something to try. I will tell more when I play some hours.

For the Mesa 6.5.3 check:

[www.mesa3d.org](www.mesa3d.org)

For how to compile and install it check:

dri.freedesktop.org

Of course you need to have the DRI (Direct Rendering) on the Mesa drivers.

I am having a Dell D600 running Kubuntu 6.10, and I have just installed Mesa 6.5.3 and also the library for ST3C extension that can be found as well through dri.freedesktop.org.

The graphics card I am using is an ATI Mobility Radeon 9000 with 32MB.

There is hope!

---

### Post by Kubunteando on 2007-05-07
Sorry, I meant the library S3TC (Texture Compression).
The Open Source drivers does not seem to implement it. It seems there is some kind of patent issue.

But with that library you can use S3TC.

---

### Post by Virgilius on 2007-06-02
I've just DL-ed the client for Regnum and it's a tar.gz. Does it mean I'll have to compile this thing? Anything that'll help? If there is, I appreciate it :)

---

### Post by MaximB on 2007-06-03
> **Virgilius said:**
> I've just DL-ed the client for Regnum and it's a tar.gz. Does it mean I'll have to compile this thing? Anything that'll help? If there is, I appreciate it :)

you don't need to compile anything, just extract it and run the installer - it will download the whole game for you and then just execute it.

---

### Post by Bob Morane on 2007-06-17
Hello, there is a nasty bug in the last version of RO. It no longer works on feisty with ati cards and fglrx drivers. I wanted to try with open-source drivers and tried to compile mesa 6.5.3 but it doesn't work.

I first did a apt-get build-dep mesa to make sure all the dependencies are met. However, when i try to compile the archive downloaded from sourceforge, i get the following output and the the "lib" directory stays empty.

```
:~/Downloads/Mesa/Mesa-6.5.3$ make linux-dri
(cd configs && rm -f current && ln -s linux-dri current)
make default
make[1]: entrant dans le répertoire « /home/roland/Downloads/Mesa/Mesa-6.5.3 »
make[2]: entrant dans le répertoire « /home/roland/Downloads/Mesa/Mesa-6.5.3/src »
Making sources for linux-dri
mkdir ../lib
make[3]: entrant dans le répertoire « /home/roland/Downloads/Mesa/Mesa-6.5.3/src/glx/x11 »
Makefile:91: depend: Aucun fichier ou répertoire de ce type
touch depend
makedepend -fdepend -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa/main -I../../../src/mesa/glapi `pkg-config --cflags libdrm` -I/usr/X11R6/include glcontextmodes.c clientattrib.c compsize.c eval.c glxcmds.c glxext.c glxextensions.c indirect.c indirect_init.c indirect_size.c indirect_window_pos.c indirect_transpose_matrix.c indirect_vertex_array.c indirect_vertex_program.c pixel.c pixelstore.c render2.c renderpix.c single2.c singlepix.c vertarr.c xfont.c glx_pbuffer.c glx_query.c glx_texture_compression.c dri_glx.c XF86dri.c \
                ../../../src/mesa/main/dispatch.c ../../../src/mesa/glapi/glapi.c ../../../src/mesa/glapi/glthread.c  
makedepend: warning:  glcontextmodes.c (reading /usr/include/bits/types.h, line 31): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  glcontextmodes.c (reading /usr/include/sys/types.h, line 147): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  glcontextmodes.c (reading /usr/include/X11/Xlib.h, line 75): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  glcontextmodes.c (reading ../../../include/GL/glext.h, line 3385): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  glcontextmodes.c (reading /usr/include/inttypes.h, line 38): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  glcontextmodes.c (reading /usr/include/string.h, line 33): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  glcontextmodes.c (reading /usr/include/stdlib.h, line 33): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  glcontextmodes.c (reading /usr/include/alloca.h, line 25): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  glcontextmodes.c (reading /usr/include/X11/Xlibint.h, line 347): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  clientattrib.c (reading /usr/include/stdio.h, line 34): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  clientattrib.c (reading /usr/include/_G_config.h, line 14): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  clientattrib.c (reading /usr/include/wchar.h, line 48): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  clientattrib.c (reading /usr/include/gconv.h, line 31): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../../../include/stddef.h
        not in ../../../include/GL/internal/stddef.h
        not in ../../../src/mesa/main/stddef.h
        not in ../../../src/mesa/glapi/stddef.h
        not in /usr/include/drm/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
makedepend: warning:  clientattrib.c (reading /usr/include/libio.h, line 53): cannot find include file "stdarg.h"
        not in ./stdarg.h
        not in ../../../include/stdarg.h
        not in ../../../include/GL/internal/stdarg.h
        not in ../../../src/mesa/main/stdarg.h
        not in ../../../src/mesa/glapi/stdarg.h
        not in /usr/include/drm/stdarg.h
        not in /usr/X11R6/include/stdarg.h
        not in /usr/include/stdarg.h
makedepend: warning:  glxcmds.c (reading /usr/include/limits.h, line 125): cannot find include file "limits.h"
makedepend: warning:  glxcmds.c (reading ../../../src/mesa/main/glheader.h, line 68): cannot find include file "float.h"
        not in ./float.h
        not in ../../../include/float.h
        not in ../../../include/GL/internal/float.h
        not in ../../../src/mesa/main/float.h
        not in ../../../src/mesa/glapi/float.h
        not in /usr/include/drm/float.h
        not in /usr/X11R6/include/float.h
        not in /usr/include/float.h
makedepend: warning:  glxcmds.c (reading ../../../src/mesa/main/glheader.h, line 69): cannot find include file "stdarg.h"
        not in ./stdarg.h
        not in ../../../include/stdarg.h
        not in ../../../include/GL/internal/stdarg.h
        not in ../../../src/mesa/main/stdarg.h
        not in ../../../src/mesa/glapi/stdarg.h
        not in /usr/include/drm/stdarg.h
        not in /usr/X11R6/include/stdarg.h
        not in /usr/include/stdarg.h
makedepend: warning:  glxext.c, line 51: cannot find include file "X11/extensions/Xfixes.h"
        not in ./X11/extensions/Xfixes.h
        not in ../../../include/X11/extensions/Xfixes.h
        not in ../../../include/GL/internal/X11/extensions/Xfixes.h
        not in ../../../src/mesa/main/X11/extensions/Xfixes.h
        not in ../../../src/mesa/glapi/X11/extensions/Xfixes.h
        not in /usr/include/drm/X11/extensions/Xfixes.h
        not in /usr/X11R6/include/X11/extensions/Xfixes.h
        not in /usr/include/X11/extensions/Xfixes.h
makedepend: warning:  glxext.c, line 52: cannot find include file "X11/extensions/Xdamage.h"
        not in ./X11/extensions/Xdamage.h
        not in ../../../include/X11/extensions/Xdamage.h
        not in ../../../include/GL/internal/X11/extensions/Xdamage.h
        not in ../../../src/mesa/main/X11/extensions/Xdamage.h
        not in ../../../src/mesa/glapi/X11/extensions/Xdamage.h
        not in /usr/include/drm/X11/extensions/Xdamage.h
        not in /usr/X11R6/include/X11/extensions/Xdamage.h
        not in /usr/include/X11/extensions/Xdamage.h
make[3]: quittant le répertoire « /home/roland/Downloads/Mesa/Mesa-6.5.3/src/glx/x11 »
make[3]: entrant dans le répertoire « /home/roland/Downloads/Mesa/Mesa-6.5.3/src/glx/x11 »
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa/main -I../../../src/mesa/glapi `pkg-config --cflags libdrm` -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/X11R6/lib/modules/dri\" glcontextmodes.c -o glcontextmodes.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa/main -I../../../src/mesa/glapi `pkg-config --cflags libdrm` -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/X11R6/lib/modules/dri\" clientattrib.c -o clientattrib.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa/main -I../../../src/mesa/glapi `pkg-config --cflags libdrm` -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/X11R6/lib/modules/dri\" compsize.c -o compsize.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa/main -I../../../src/mesa/glapi `pkg-config --cflags libdrm` -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/X11R6/lib/modules/dri\" eval.c -o eval.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa/main -I../../../src/mesa/glapi `pkg-config --cflags libdrm` -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/X11R6/lib/modules/dri\" glxcmds.c -o glxcmds.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa/main -I../../../src/mesa/glapi `pkg-config --cflags libdrm` -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/X11R6/lib/modules/dri\" glxext.c -o glxext.o
glxext.c:51:35: erreur: X11/extensions/Xfixes.h : Aucun fichier ou répertoire de ce type
glxext.c:52:36: erreur: X11/extensions/Xdamage.h : Aucun fichier ou répertoire de ce type
glxext.c:781: attention : initialization from incompatible pointer type
glxext.c:783: attention : initialization from incompatible pointer type
glxext.c:788: attention : initialization from incompatible pointer type
glxext.c:791: attention : initialization from incompatible pointer type
glxext.c:793: attention : initialization from incompatible pointer type
make[3]: *** [glxext.o] Erreur 1
make[3]: quittant le répertoire « /home/roland/Downloads/Mesa/Mesa-6.5.3/src/glx/x11 »
make[2]: *** [subdirs] Erreur 1
make[2]: quittant le répertoire « /home/roland/Downloads/Mesa/Mesa-6.5.3/src »
make[1]: *** [default] Erreur 1
make[1]: quittant le répertoire « /home/roland/Downloads/Mesa/Mesa-6.5.3 »
make: *** [linux-dri] Erreur 2

```

I also tryed to follow the freedesktop wiki, but i can't grab drm with git.
```
~/Downloads/Mesa$ git clone git://anongit.freedesktop.org/git/mesa/drm

git, the filemanager with GNU Interactive Tools, is now called gitfm.

If you are looking for git, Linus Torvald's content tracker, install
the cogito and git-core packages and see README.Debian and git(7).

This transition script will be removed in the debian stable
release after etch.

If you wish to complete the transition early, install git-core
and use (as root):
 update-alternatives --config git

Press RETURN to run gitfm


GNU Interactive Tools 4.3.20 (i686-pc-linux-gnu), 16:31:59 Nov  9 2006
GIT is free software; you can redistribute it and/or modify it under the
terms of the GNU General Public License as published by the Free Software
Foundation; either version 2, or (at your option) any later version.
Copyright (C) 1993-1999 Free Software Foundation, Inc.
Written by Tudor Hulubei and Andrei Pitis, Bucharest, Romania

/usr/bin/gitfm: fatal error: `chdir' failed: permission denied.

```

---

### Post by 16777216 on 2007-06-17
As far as the graphics and sound go this is a good game. 
But I stopped playing it due to the anti-Pagan/Wiccan dialogs spread throughout the game.
If that changes I will go back.

---

### Post by JMO707 on 2007-06-17
> **16777216 said:**
> As far as the graphics and sound go this is a good game. 
But I stopped playing it due to the anti-Pagan/Wiccan dialogs spread throughout the game.
If that changes I will go back.

Uh... what do you mean? :o

---

### Post by 16777216 on 2007-06-17
Talk of destroying evil witches. Sounds pretty anti-Wiccan to me husband of a Wiccan  and  Pagan myself.

---

### Post by Kubunteando on 2007-06-17
If you are trying to compile MESA 6.5.3 (like Bob for example), the libdrm is in Feisty repositories. Install libdrm2 and libdrm-dev (you need the libdrm-dev for the compilation)

---

### Post by merlyn on 2007-06-17
> **16777216 said:**
> Talk of destroying evil witches. Sounds pretty anti-Wiccan to me husband of a Wiccan  and  Pagan myself.

Odd stance for a fantasy style game that offers Mages, both Warlocks and Conjurers as character options, seems a Medieval mindset.

The term [Pagan]("http://www.religioustolerance.org/paganism.htm") is unfortunately often deemed to have a negative conotation.

I find it useful in such cases to look at the historical meaning of words in order to cultivate a more objective appreciation.

Cheers.

---

### Post by stangbang on 2007-06-17
> **Bob Morane said:**
> Hello, there is a nasty bug in the last version of RO. It no longer works on feisty with ati cards and fglrx drivers. 

Go into options and select force video safe mode. this will let you play.

---

### Post by JMO707 on 2007-06-17
> **16777216 said:**
> Talk of destroying evil witches. Sounds pretty anti-Wiccan to me husband of a Wiccan  and  Pagan myself.

I didnt hear of anything like that, but it can very well be a term with sense inside the game, that is used in that context. Anyway, its a game with no-too-much-effort on reality emulation :p

---

### Post by 16777216 on 2007-06-18
My wife and I could over look it due to as you say medieval times and such and we can understand this.

But, my wife and five children and I live in the "Bible belt" and we all have had ill words, harassment, threats, etc...

While playing one night and my 9 year old daughter was watching when I discovered this dialog and my daughter said "Great, even the people in the games want us dead."

This is clearly a problem for us, it may not be for you.

My post was meant more as a warning than a bash on an otherwise good game.

---

### Post by JMO707 on 2007-06-18
I see =o
I dont know to much of the place you live, but yay, that must not be nice at all :s

---

### Post by Josey on 2007-06-18
> **16777216 said:**
> My wife and I could over look it due to as you say medieval times and such and we can understand this.

But, my wife and five children and I live in the "Bible belt" and we all have had ill words, harassment, threats, etc...

While playing one night and my 9 year old daughter was watching when I discovered this dialog and my daughter said "Great, even the people in the games want us dead."

This is clearly a problem for us, it may not be for you.

My post was meant more as a warning than a bash on an otherwise good game.

Considering the somewhat poor English translation I wouldn't take the dialog too seriously.

---

### Post by airtonix on 2007-06-19
as i am unable to get this great game working in my feisty running beryl on an ati9600 rv350.....i am forced to use the basement windows.....(if someone can help me i would appreciate it)..

but anyway...here i am in the dozer...on regnum. and its pretty cool. 
same name as here....on the green flag realm....hehe sorry dont know what the name is..

adios

---

### Post by merlyn on 2007-06-20
> **16777216 said:**
> My wife and I could over look it due to as you say medieval times and such and we can understand this.
 
But, my wife and five children and I live in the "Bible belt" and we all have had ill words, harassment, threats, etc...
 
While playing one night and my 9 year old daughter was watching when I discovered this dialog and my daughter said "Great, even the people in the games want us dead."
 
This is clearly a problem for us, it may not be for you.
 
My post was meant more as a warning than a bash on an otherwise good game.
 
I think you misunderstood me, I am sympathetic to your situation, hence my comment about how unusual it seems, for such sentiments to be expressed in game, as it is possible to create 'spellcasting' characters.
 
I would have hoped that my link to the meaning of the term Pagan on the Religious Tolerance site would have cleared this up.
 
Cheers.

---

### Post by po0f on 2007-06-20
I love this game.  I had never played an MMO before; within hours, I was addicted.  :)

St Alia, Syrtis conjurer

---

### Post by Duo Maxwell on 2007-07-01
> **16777216 said:**
> As far as the graphics and sound go this is a good game. 
But I stopped playing it due to the anti-Pagan/Wiccan dialogs spread throughout the game.
If that changes I will go back.


Odd, what kingdom did you join? I'm playing in Ignis, the story from there is that they are th exiled necromancers from Syrtis, outsiders are pretty much universally considerd to be heritics as they don't follow the ways of necromancy.

Tho I don't get the god monsters tho, that run around and kill their own kind like Graj, the god of the Igeno demon looking things or Jideniah, the Hyena god. But it is fun watching Jid trying to attack the Ignis resident badass, Tenax, the dragon that eats everyone lol.

---

### Post by MaximB on 2007-07-02
is it just me, or since the "final release" the game become much more buggy and practically unplayable (it crashes every 2 minutes if you have the luck to enter the game) ?

---

### Post by Duo Maxwell on 2007-07-02
You running Ubuntu studio? I had more instability on that then I did my old install of 6.06, most instability problems can be fixed by reinstaling the game, just nuke the installer and the game folder, then grab the installer again from their site.

Setting the game to download all game data at once helped a little with stability as well, be warned tho, it's like a 500Mb download to grab all of it.

---

### Post by clblanchard on 2007-07-08
> **SBFC said:**
> So...am I totally blind or is there no buddy list in Regnum?

There should be now, but it's command line type.  in the chat box type

/buddy nameofplayer = and player to list

/remove nameofplayer = remove player from list

/list = gives list of buddies

/chat nameofplayer = request chat session

hope that helps

---

### Post by Eggnog on 2007-07-22
I think I'm going to give this one a try.  Any tips for a realm, or a decent char for a beginning player?  Is it difficult to find English-speaking players?  Anything other tips for a beginner?

---

### Post by Beren Camlost on 2007-07-22
Installed, registered and patched the game without problems. However, after logging in the game crashes and this is the output of crash_backtrace_30478.log:

```

libs/libcore_client.so(_ZN10ClientBase14save_backtraceEv+0x7e) [0xb7dd140e]
libs/libcore_client.so(_ZN10ClientBase12client_crashEi+0x17) [0xb7dd17b7]
[0xffffe420]
libs/libregnum_client.so(_ZN10GameClient4initEiPPc+0x964) [0xb7f73e54]
libs/libregnum_client.so(_ZN10GameClientC1EiPPc+0xc8) [0xb7f74c48]
./game(main+0x37) [0x8048b57]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb704febc]
./game(__gxx_personality_v0+0x61) [0x8048a81]
```

Running Kubuntu Feisty, nVidia 7800GT, using the nvidia proprietary driver.

Any suggestions?

Edit: Nevermind, launching it a second time did the trick :p

---

### Post by Duo Maxwell on 2007-07-23
Tips for beginers? I'm in the Ignis realm, but first thing to do when you start a new char is to talk to all the npcs at the starting place, they will tell you to do a few things, like find this person, kill this and go here, you'll know who you're supposed to talk to cause they'll have a yellow exclamation point over their heads.

When making a new char take a look at what stat differences there are between races and classes, some are better suited then others for certain classes but all will do fine, but pick your starting stats wisely, you can not change those 5 starting points at all once you've made your char.

You don't have to buy new gear every time it's availble, nor should you always repair it at every chance, if its going to break yeah, but not every time you go to unload the critter guts you get from kills.

Non weapon mob drops aren't useful for anything as of yet, no word if theres going to be a crafting system implemented yet, so just hock it for gold.

Gold shouldn't be an issue for any player till after around Lv30, the lv that you start being effective in war, as in you wont be killed in 5 seconds by a lone player, 37 is about when you get the really good spells tho. Infact cash is so easy to come by that I still have all my better then normal gear that I had bought, got from drops or recived as gifts from other playersmy normal and under grade ger I either gave away as gifts or sold id noone wanted it and yet my knight still had 300+k in the wad at Lv30 from quests and mob drops.

classes, there are 3 starting classes and 2 advanced jobs for each that you can change to permanently or not at all starting at Lv10, warriors can become knights, insane defence and blocking or barbarian, unimaginible attack strenght.

Mages, you can become a Conjurer, you can heal, summon things to fight for you, everyone loves you, especially your enemies in the war zone, warlocks, the nuclear ordinance class, you can lay waste to vast areas at once, but don't let your abilities go to your head, they can get you into more trouble then they get you out of.

 
Archers, you can become a marksmen, you're the high percision damage dealer that can pick someone off from miles away before they even know where it's comming from. Or theres Hunters, you're the indian tracker / ninja guy, you can track anyone nearly anywhere, very handy when you want to get the drop on your opponents in war as well as go invisible if things get out of hand. You can also tame monsters and use them to do your bidding as well, not as useful as a summon tho sine you can't heal it, but useful for softening up your target in war.

look me up on Ignis, Duo Maxwell Lv32 Knight, Yo Momma, Lv31 Conjurer and Izana, Lv15 Hunter


Almost forgot, when you start you can have 3 chars per an account, but that account can opnly be logged on on one machine at a time, and you can also only be in the realm you picked for all 3 chars, to help curb the reluctance some would have to not wanting to fight their friends from one realm to another.

---

### Post by po0f on 2007-07-23
Eggnog,

Duo Maxwell summed it up well.  I guess I can forgive him for being Ignis.  :)

St Alia, Syrtian conjurer

---

### Post by Ludford on 2007-07-23
Is it ciick to move or WASD to move?

---

### Post by Duo Maxwell on 2007-07-23
wasd and arrows, click and move isn't too useful when I can just hit q and auto run.

---

### Post by sochbat on 2007-07-25
this is annoyin.  I've installed the game, but whe i load it up, my screen blanks out.  My resolution and everything seems peachy.

any hints on trouble shooting?

---

### Post by donkyhotay on 2007-07-26
Anyone managed to get regnum working on 64bit feisty?

---

### Post by Southeast First on 2007-08-26
I figured I'd post in this thread instead of making a new one. Can anyone help me? Whenever I try to run Regnum terminal pulls this out:

> *** glibc detected *** ./rolauncher: free(): invalid pointer: 0x08666860 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb77eed75]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb77f2810]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb76fe8c1]
./rolauncher[0x817613d]
./rolauncher[0x8070b53]
./rolauncher[0x8065a7a]
./rolauncher[0x8067ed1]
./rolauncher[0x810074e]
./rolauncher[0x805c55e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb779b050]
./rolauncher(__gxx_personality_v0+0x3d5)[0x805c391]
======= Memory map: ========
08048000-0840e000 r-xp 00000000 03:01 16238166   /home/blackjaw/.Games/Regnum/rolauncher
0840e000-0844b000 rw-p 003c6000 03:01 16238166   /home/blackjaw/.Games/Regnum/rolauncher
0844b000-08694000 rw-p 0844b000 00:00 0          [heap]
b6600000-b6621000 rw-p b6600000 00:00 0 
b6621000-b6700000 ---p b6621000 00:00 0 
b67cc000-b6858000 r--p 00000000 03:01 22200501   /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6858000-b685a000 r-xp 00000000 03:01 165575     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b685a000-b685b000 rw-p 00001000 03:01 165575     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b685b000-b685e000 r--s 00000000 03:01 7524064    /var/cache/fontconfig/5e10083637a12ecd1bff191eb66bfa2f-x86.cache-2
b685e000-b6860000 r--s 00000000 03:01 7524136    /var/cache/fontconfig/603b2eb47209ddb3c5269b217a306167-x86.cache-2
b6860000-b6866000 r--s 00000000 03:01 7524135    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b6866000-b6869000 r--s 00000000 03:01 7524133    /var/cache/fontconfig/a46337af8a0b4c9b317ad981ec3bdf87-x86.cache-2
b6869000-b686a000 r--s 00000000 03:01 7524131    /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b686a000-b686d000 r--s 00000000 03:01 7524130    /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b686d000-b686e000 r--s 00000000 03:01 7524129    /var/cache/fontconfig/6edd069ccec3ba28096b368c434fa861-x86.cache-2
b686e000-b686f000 r--s 00000000 03:01 7524128    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b686f000-b6870000 r--s 00000000 03:01 7524127    /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b6870000-b6874000 r--s 00000000 03:01 7524126    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b6874000-b6875000 r--s 00000000 03:01 7524125    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b6875000-b6890000 r--s 00000000 03:01 7524124    /var/cache/fontconfig/4ca92cf76c0cf3dfa7f011127eff595d-x86.cache-2
b6890000-b68ac000 r--s 00000000 03:01 7524123    /var/cache/fontconfig/6abf76b0b4cc7192703d8431ac929b75-x86.cache-2
b68ac000-b68ca000 r--s 00000000 03:01 7524122    /var/cache/fontconfig/f408d08d2fce062ab660f628db78bf96-x86.cache-2
b68ca000-b68cb000 r--s 00000000 03:01 7524121    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b68cb000-b68cd000 r--s 00000000 03:01 7524120    /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b68cd000-b68cf000 r--s 00000000 03:01 7524119    /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b68cf000-b68d0000 r--s 00000000 03:01 7524095    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b68d0000-b68d1000 r--s 00000000 03:01 7524087    /var/cache/fontconfig/a8d35ba226d862df35f7c320f882e11a-x86.cache-2
b68d1000-b68d3000 r--s 00000000 03:01 7524085    /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b68d3000-b68d9000 r--s 00000000 03:01 7524084    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b68d9000-b68db000 r--s 00000000 03:01 7524082    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b68db000-b68dd000 r--s 00000000 03:01 7524081    /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b68dd000-b68e5000 r--s 00000000 03:01 7524079    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b68e5000-b68eb000 r--s 00000000 03:01 7524078    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b68eb000-b68ec000 r--s 00000000 03:01 7524077    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b68ec000-b6903000 r--s 00000000 03:01 7524076    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b6903000-b6905000 r--s 00000000 03:01 7524075    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b6905000-b690b000 r--s 00000000 03:01 7523911    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b690b000-b690f000 r--s 00000000 03:01 7520909    /var/cache/fontconfig/105b9c7e6f0a4f82d8c9b6e39c52c6f9-x86.cache-2
b690f000-b6912000 r--s 00000000 03:01 7523839    /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b6912000-b6916000 r--s 00000000 03:01 7523838    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b6916000-b691d000 r--s 00000000 03:01 7524118    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b691d000-b691e000 r--s 00000000 03:01 7524112    /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b691e000-b691f000 r--s 00000000 03:01 7524110    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b691f000-b6920000 r--s 00000000 03:01 7524109    /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b6920000-b6921000 r--s 00000000 03:01 7524156    /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
b6921000-b6922000 r--s 00000000 03:01 7524155    /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86.cache-2
b6922000-b6925000 r--s 00000000 03:01 7524154    /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b6925000-b6929000 r--s 00000000 03:01 7524153    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b6929000-b6932000 r--s 00000000 03:01 7524152    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b6932000-b6935000 r--s 00000000 03:01 7524117    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b6935000-b6936000 r--s 00000000 03:01 7524151    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b6936000-b6938000 r--s 00000000 03:01 7524008    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b6938000-b6939000 r--s 00000000 03:01 7524115    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b6939000-b693e000 r--s 00000000 03:01 7524148    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b693e000-b6943000 r--s 00000000 03:01 7524091    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b6943000-b6949000 r--s 00000000 03:01 7524146    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b6949000-b694c000 r--s 00000000 03:01 7524145    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b694c000-b694d000 r--s 00000000 03:01 7524144    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b694d000-b694f000 r--s 00000000 03:01 7524143    /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86.cache-2
b694f000-b6951000 r--s 00000000 03:01 7524142    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b6951000-b6957000 r--s 00000000 03:01 7524141    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b6957000-b695d000 r--s 00000000 03:01 7524116    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b695d000-b695e000 r--s 00000000 03:01 7520986    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b695e000-b6967000 r--s 00000000 03:01 7523949    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b6967000-b696d000 r--s 00000000 03:01 7523948    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b696d000-b6992000 r-xp 00000000 03:01 20758534   /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6992000-b6993000 rw-p 00025000 03:01 20758534   /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6993000-b6994000 ---p b6993000 00:00 0 
b6994000-b7194000 rwxp b6994000 00:00 0 
b7194000-b71b5000 rw-p b7194000 00:00 0 
b71b5000-b71be000 r-xp 00000000 03:01 7310399    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b71be000-b71c0000 rw-p 00008000 03:01 7310399    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b71c0000-b71c8000 r-xp 00000000 03:01 7310401    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b71c8000-b71ca000 rw-p 00007000 03:01 7310401    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b71ca000-b71de000 r-xp 00000000 03:01 7310396    /lib/tls/i686/cmov/libnsl-2.6.1.so
b71de000-b71e0000 rw-p 00013000 03:01 7310396    /lib/tls/i686/cmov/libnsl-2.6.1.so
b71e0000-b71e2000 rw-p b71e0000 00:00 0 
b71e2000-b71e9000 r-xp 00000000 03:01 7310397    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b71e9000-b71eb000 rw-p 00006000 03:01 7310397    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b71ee000-b71f2000 r--s 00000000 03:01 7524071    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b71f2000-b71f7000 r--s 00000000 03:01 7524070    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b71f7000-b71f8000 r--s 00000000 03:01 7524011    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-x86.cache-2
b71f8000-b71f9000 r-xp 00000000 03:01 20677484   /usr/lib/gconv/ISO8859-1.so
b71f9000-b71fb000 rw-p 00000000 03:01 20677484   /usr/lib/gconv/ISO8859-1.so
b71fb000-b71fc000 r--p 00000000 03:01 164205     /usr/lib/locale/en_US.utf8/LC_NUMERIC
b71fc000-b71fd000 r--p 00000000 03:01 164476     /usr/lib/locale/en_US.utf8/LC_TIME
b71fd000-b72dd000 r--p 00000000 03:01 164475     /usr/lib/locale/en_US.utf8/LC_COLLATE
b72dd000-b72de000 r--p 00000000 03:01 164477     /usr/lib/locale/en_US.utf8/LC_MONETARY
b72de000-b72df000 r--p 00000000 03:01 164210     /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b72df000-b72e0000 r--p 00000000 03:01 164231     /usr/lib/locale/en_US.utf8/LC_PAPER
b72e0000-b731f000 r--p 00000000 03:01 164474     /usr/lib/locale/en_US.utf8/LC_CTYPE
b731f000-b7321000 rw-p b731f000 00:00 0 
b7321000-b7343000 r-xp 00000000 03:01 20661267   /usr/lib/libpng12.so.0.15.0
b7343000-b7344000 rw-p 00021000 03:01 20661267   /usr/lib/libpng12.so.0.15.0
b7344000-b7345000 rw-p b7344000 00:00 0 
b7345000-b73b0000 r-xp 00000000 03:01 14451540   /usr/lib/libfreetype.so.6.3.16
b73b0000-b73b4000 rw-p 0006a000 03:01 14451540   /usr/lib/libfreetype.so.6.3.16
b73b4000-b73e1000 r-xp 00000000 03:01 20661157   /usr/lib/libpangoft2-1.0.so.0.1800.0
b73e1000-b73e2000 rw-p 0002c000 03:01 20661157   /usr/lib/libpangoft2-1.0.so.0.1800.0
b73e2000-b73e6000 r-xp 00000000 03:01 20660677   /usr/lib/libXdmcp.so.6.0.0
b73e6000-b73e7000 rw-p 00003000 03:01 20660677   /usr/lib/libXdmcp.so.6.0.0
b73e7000-b73fc000 r-xp 00000000 03:01 20661380   /usr/lib/libICE.so.6.3.0
b73fc000-b73fe000 rw-p 00014000 03:01 20661380   /usr/lib/libICE.so.6.3.0
b73fe000-b7400000 rw-p b73fe000 00:00 0 
b7400000-b7402000 r-xp 00000000 03:01 20661205   /usr/lib/libXau.so.6.0.0
b7402000-b7403000 rw-p 00001000 03:01 20661205   /usr/lib/libXau.so.6.0.0
b7403000-b740b000 r-xp 00000000 03:01 20661222   /usr/lib/libXcursor.so.1.0.2
b740b000-b740c000 rw-p 00007000 03:01 20661222   /usr/lib/libXcursor.so.1.0.2
b740c000-b7411000 r-xp 00000000 03:01 20661245   /usr/lib/libXrandr.so.2.1.0
b7411000-b7412000 rw-p 00005000 03:01 20661245   /usr/lib/libXrandr.so.2.1.0
b7412000-b7419000 r-xp 00000000 03:01 20661226   /usr/lib/libXi.so.6.0.0
b7419000-b741a000 rw-p 00006000 03:01 20661226   /usr/lib/libXi.so.6.0.0
b741a000-b7421000 r-xp 00000000 03:01 20660979   /usr/lib/libXrender.so.1.3.0
b7421000-b7422000 rw-p 00006000 03:01 20660979   /usr/lib/libXrender.so.1.3.0
b7422000-b7423000 rw-p b7422000 00:00 0 
b7423000-b7446000 r-xp 00000000 03:01 20660564   /usr/lib/libfontconfig.so.1.2.0
b7446000-b744e000 rw-p 00023000 03:01 20660564   /usr/lib/libfontconfig.so.1.2.0
b744e000-b74c2000 r-xp 00000000 03:01 14451596   /usr/lib/libcairo.so.2.11.5
b74c2000-b74c4000 rw-p 00074000 03:01 14451596   /usr/lib/libcairo.so.2.11.5
b74c4000-b74c7000 r-xp 00000000 03:01 14451209   /usr/lib/libgmodule-2.0.so.0.1400.0
b74c7000-b74c8000 rw-p 00002000 03:01 14451209   /usr/lib/libgmodule-2.0.so.0.1400.0
b74c8000-b74e1000 r-xp 00000000 03:01 14451230   /usr/lib/libatk-1.0.so.0.1915.1
b74e1000-b74e3000 rw-p 00018000 03:01 14451230   /usr/lib/libatk-1.0.so.0.1915.1
b74e3000-b74e7000 r-xp 00000000 03:01 20661173   /usr/lib/libXfixes.so.3.1.0
b74e7000-b74e8000 rw-p 00003000 03:01 20661173   /usr/lib/libXfixes.so.3.1.0
b74e8000-b74ea000 r-xp 00000000 03:01 20660342   /usr/lib/libXdamage.so.1.1.0
b74ea000-b74eb000 rw-p 00001000 03:01 20660342   /usr/lib/libXdamage.so.1.1.0
b74eb000-b74ec000 rw-p b74eb000 00:00 0 
b74ec000-b74ee000 r-xp 00000000 03:01 20661213   /usr/lib/libXcomposite.so.1.0.0
b74ee000-b74ef000 rw-p 00001000 03:01 20661213   /usr/lib/libXcomposite.so.1.0.0
b74ef000-b74f7000 r-xp 00000000 03:01 20661154   /usr/lib/libpangocairo-1.0.so.0.1800.0
b74f7000-b74f8000 rw-p 00007000 03:01 20661154   /usr/lib/libpangocairo-1.0.so.0.1800.0
b74f8000-b74ff000 r-xp 00000000 03:01 7310406    /lib/tls/i686/cmov/librt-2.6.1.so
b74ff000-b7501000 rw-p 00006000 03:01 7310406    /lib/tls/i686/cmov/librt-2.6.1.so
b7501000-b751f000 r-xp 00000000 03:01 20660470   /usr/lib/libexpat.so.1.0.0
b751f000-b7521000 rw-p 0001e000 03:01 20660470   /usr/lib/libexpat.so.1.0.0
b7521000-b7535000 r-xp 00000000 03:01 14451523   /usr/lib/libz.so.1.2.3.3
b7535000-b7536000 rw-p 00013000 03:01 14451523   /usr/lib/libz.so.1.2.3.3
b7536000-b7537000 rw-p b7536000 00:00 0 
b7537000-b753e000 r-xp 00000000 03:01 20661390   /usr/lib/libSM.so.6.0.0
b753e000-b753f000 rw-p 00006000 03:01 20661390   /usr/lib/libSM.so.6.0.0
b753f000-b7541000 r-xp 00000000 03:01 20661235   /usr/lib/libXinerama.so.1.0.0
b7541000-b7542000 rw-p 00001000 03:01 20661235   /usr/lib/libXinerama.so.1.0.0
b7542000-b7544000 r-xp 00000000 03:01 7310393    /lib/tls/i686/cmov/libdl-2.6.1.so
b7544000-b7546000 rw-p 00001000 03:01 7310393    /lib/tls/i686/cmov/libdl-2.6.1.so
b7546000-b7580000 r-xp 00000000 03:01 14451211   /usr/lib/libgobject-2.0.so.0.1400.0
b7580000-b7581000 rw-p 0003a000 03:01 14451211   /usr/lib/libgobject-2.0.so.0.1400.0
b7581000-b766e000 r-xp 00000000 03:01 20661112   /usr/lib/libX11.so.6.2.0
b766e000-b7672000 rw-p 000ed000 03:01 20661112   /usr/lib/libX11.so.6.2.0
b7672000-b76ad000 r-xp 00000000 03:01 20660423   /usr/lib/libpango-1.0.so.0.1800.0
b76ad000-b76af000 rw-p 0003b000 03:01 20660423   /usr/lib/libpango-1.0.so.0.1800.0
b76af000-b76b0000 rw-p b76af000 00:00 0 
b76b0000-b76c7000 r-xp 00000000 03:01 14450773   /usr/lib/libgdk_pixbuf-2.0.so.0.1106.0
b76c7000-b76c8000 rw-p 00016000 03:01 14450773   /usr/lib/libgdk_pixbuf-2.0.so.0.1106.0
b76c8000-b7784000 r-xp 00000000 03:01 14451207   /usr/lib/libglib-2.0.so.0.1400.0
b7784000-b7785000 rw-p 000bc000 03:01 14451207   /usr/lib/libglib-2.0.so.0.1400.0
b7785000-b78c9000 r-xp 00000000 03:01 7310390    /lib/tls/i686/cmov/libc-2.6.1.so
b78c9000-b78ca000 r--p 00143000 03:01 7310390    /lib/tls/i686/cmov/libc-2.6.1.so
b78ca000-b78cc000 rw-p 00144000 03:01 7310390    /lib/tls/i686/cmov/libc-2.6.1.so
b78cc000-b78cf000 rw-p b78cc000 00:00 0 
b78cf000-b78d9000 r-xp 00000000 03:01 7274568    /lib/libgcc_s.so.1
b78d9000-b78da000 rw-p 0000a000 03:01 7274568    /lib/libgcc_s.so.1
b78da000-b78fd000 r-xp 00000000 03:01 7310394    /lib/tls/i686/cmov/libm-2.6.1.so
b78fd000-b78ff000 rw-p 00023000 03:01 7310394    /lib/tls/i686/cmov/libm-2.6.1.so
b78ff000-b79e7000 r-xp 00000000 03:01 20660922   /usr/lib/libstdc++.so.6.0.9
b79e7000-b79ea000 r--p 000e8000 03:01 20660922   /usr/lib/libstdc++.so.6.0.9
b79ea000-b79ec000 rw-p 000eb000 03:01 20660922   /usr/lib/libstdc++.so.6.0.9
b79ec000-b79f3000 rw-p b79ec000 00:00 0 
b79f3000-b7a40000 r-xp 00000000 03:01 20660443   /usr/lib/libXt.so.6.0.0
b7a40000-b7a44000 rw-p 0004c000 03:01 20660443   /usr/lib/libXt.so.6.0.0
b7a44000-b7a51000 r-xp 00000000 03:01 20660972   /usr/lib/libXext.so.6.4.0
b7a51000-b7a52000 rw-p 0000d000 03:01 20660972   /usr/lib/libXext.so.6.4.0
b7a52000-b7a56000 r-xp 00000000 03:01 20661320   /usr/lib/libXxf86vm.so.1.0.0
b7a56000-b7a57000 rw-p 00003000 03:01 20661320   /usr/lib/libXxf86vm.so.1.0.0
b7a57000-b7aef000 r-xp 00000000 03:01 14483523   /usr/lib/libGL.so.1.2
b7aef000-b7af4000 rw-p 00098000 03:01 14483523   /usr/lib/libGL.so.1.2
b7af4000-b7af7000 rw-p b7af4000 00:00 0 
b7af7000-b7b84000 r-xp 00000000 03:01 20660303   /usr/lib/libgdk-x11-2.0.so.0.1106.0
b7b84000-b7b87000 rw-p 0008c000 03:01 20660303   /usr/lib/libgdk-x11-2.0.so.0.1106.0
b7b87000-b7f38000 r-xp 00000000 03:01 14450775   /usr/lib/libgtk-x11-2.0.so.0.1106.0
b7f38000-b7f3e000 rw-p 003b1000 03:01 14450775   /usr/lib/libgtk-x11-2.0.so.0.1106.0
b7f3e000-b7f40000 rw-p b7f3e000 00:00 0 
b7f40000-b7f44000 r-xp 00000000 03:01 14451213   /usr/lib/libgthread-2.0.so.0.1400.0
b7f44000-b7f45000 rw-p 00003000 03:01 14451213   /usr/lib/libgthread-2.0.so.0.1400.0
b7f45000-b7f59000 r-xp 00000000 03:01 7310404    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7f59000-b7f5b000 rw-p 00013000 03:01 7310404    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7f5b000-b7f5d000 rw-p b7f5b000 00:00 0 
b7f5d000-b7f5e000 r--p 00000000 03:01 164240     /usr/lib/locale/en_US.utf8/LC_NAME
b7f5e000-b7f5f000 r--p 00000000 03:01 164478     /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7f5f000-b7f60000 r--p 00000000 03:01 164479     /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7f60000-b7f61000 r--p 00000000 03:01 164480     /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7f61000-b7f62000 r--p 00000000 03:01 164481     /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7f62000-b7f64000 r-xp 00000000 03:01 20677669   /usr/lib/gconv/UTF-32.so
b7f64000-b7f66000 rw-p 00001000 03:01 20677669   /usr/lib/gconv/UTF-32.so
b7f66000-b7f6d000 r--s 00000000 03:01 20676677   /usr/lib/gconv/gconv-modules.cache
b7f6d000-b7f6f000 rw-p b7f6d000 00:00 0 
b7f6f000-b7f89000 r-xp 00000000 03:01 7274527    /lib/ld-2.6.1.so
b7f89000-b7f8b000 rw-p 00019000 03:01 7274527    /lib/ld-2.6.1.so
bff6e000-bff81000 rwxp bff6e000 00:00 0          [stack]
bff81000-bff84000 rw-p bff81000 00:00 0 
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)


---

### Post by Dark Star on 2007-08-26
Just played this game on my frnd PC and it is awesome :)

---

### Post by omgsplod on 2007-08-26
Someone should make a guild, If they haven't already. I'm sorry, I just dont have the time to read this whole thread, but you could obviously make an English speaking clan, possibly consisting mostly of Linux users :). I downloaded this a few days ago, but haven't done a lot of playing, considering I'm a bit busy lately and It's not as entertaining without ease of communication :<

---

### Post by Bokonon on 2007-08-27
> **donkyhotay said:**
> Anyone managed to get regnum working on 64bit feisty?

They have a 64 bit client that worked for me incl sound.

Check the bottom of page 5 for the link.  
[http://www.regnumonline.com.ar/forum/showthread.php?t=1617&page=5&highlight=linux](http://www.regnumonline.com.ar/forum/showthread.php?t=1617&page=5&highlight=linux)

---

### Post by Ferrat on 2007-08-27
Southeast First I have the same problem and get the same msg, just updated to gutsy, worked in fiesty but now I crash with exactly the same as you 

My guess woul be something to do with the tls but other than that, I don't know >_<

---

### Post by j.miller565 on 2007-08-28
I think a Linux Regnum Clan (LRC or something) would be awesome!! Right now 
I'm a Level 11,  Dark Elf Warlock

---

### Post by Anpu on 2007-09-21
Hi, I have problem with Regnum. I have ATI 9250, and I cannot run this game, after log in, i got this window error:
There are three possible causes for this error:
1. Your video card is too old
2. You haven't installed the latest available drivers
3. You haven't installed the latest DirectX version"

I installed DRIconf, but when I start it, it says:
Could not detect any configurable direct-rendering capable devices. DRIconf will be started in expert mode.

And then it opens window with 2 files listed from left side. Thats it. In console it says:
Driver "r200" is not installed or does not support configuration.

I have Mesa 7.0.1 installed. 

Does anyone know how to solve this problem? Just dont suggest to buy new card, cause this card works very good, except with Regnum. 
ty :)

---

### Post by Anpu on 2007-09-22
Problem solved, thx anyway :)

---

### Post by r3ymysterio9 on 2007-09-28
ive been thinking bout playin it, is it good?  :confused:

---

### Post by timjayko on 2007-09-28
Regnum is so far the coolest free MMORPG out there that runs in linux natively

---

### Post by Goronok on 2007-10-15
> **Southeast First said:**
> I figured I'd post in this thread instead of making a new one. Can anyone help me? Whenever I try to run Regnum terminal pulls this out:


I have a very similar problem.  When i run the installer for RO, i get a :

*** glibc detected *** ./rolauncher: free(): invalid pointer: 0x08643ba0 ***

and the installer never opens.  Has anyone else seen this, or know a possible fix? 

I'm currently running the Gutsy beta.

---

### Post by Goronok on 2007-10-15
Answered my own question after searching around.  For those seeing these errors,  try this :

G_SLICE=always-malloc ./rolauncher

in your regnum directory of course.

---

### Post by jaybombalous on 2007-10-15
thank you for this tip

---

### Post by Mayfairy on 2007-10-26
Thanks for this tip Goronok. Going to paste it here in my post so I can later return to it by "Find all your posts" function. :P 
Going to forget how to launch the game anyways. 

"G_SLICE=always-malloc ./rolauncher"

---

### Post by Mayfairy on 2007-10-26
I'm trying to launch Regnum Online and after I insert my login and password I get an error screen:

Unsupported video card!
There are three possible causes for this error:
1. Your video card is too old
2. You haven't installed the latest available drivers
3. You haven't installed the latest DirectX version

And terminal says the following:
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".

I'm running Ubuntu Gutsy and have Nvidia 6600 card with 'nvidia-glx-new' drivers installed and enabled. Compiz Fusion runs nicely and everything. Just this game doesn't. 

When I try 'apt-get install xorg-driver-fglrx' it wants to remove my nvidia-glx-new. Any ideas what to do?

---

### Post by raydeen on 2007-10-26
> **Mayfairy said:**
> I'm trying to launch Regnum Online and after I insert my login and password I get an error screen:

Unsupported video card!
There are three possible causes for this error:
1. Your video card is too old
2. You haven't installed the latest available drivers
3. You haven't installed the latest DirectX version

And terminal says the following:
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".

I'm running Ubuntu Gutsy and have Nvidia 6600 card with 'nvidia-glx-new' drivers installed and enabled. Compiz Fusion runs nicely and everything. Just this game doesn't. 

When I try 'apt-get install xorg-driver-fglrx' it wants to remove my nvidia-glx-new. Any ideas what to do?

I'm getting the same thing. ATI x1400.

---

### Post by Mayfairy on 2007-10-27
> **raydeen said:**
> I'm getting the same thing. ATI x1400.

For you it should be easy. Do 'sudo apt-get install xorg-driver-flgrx' to install ATI drivers.

---

### Post by raydeen on 2007-10-27
> **Mayfairy said:**
> For you it should be easy. Do 'sudo apt-get install xorg-driver-flgrx' to install ATI drivers.

I believe I already have that installed. I get 3D acceleration with Compiz, screensavers, games like PlanetPenguin, etc. I'll try again in a month or so when maybe ATI will have a decent driver release. I tried the latest one and it was quite the stinker performance wise.

---

### Post by Mayfairy on 2007-10-28
> **raydeen said:**
> I believe I already have that installed. I get 3D acceleration with Compiz, screensavers, games like PlanetPenguin, etc. I'll try again in a month or so when maybe ATI will have a decent driver release. I tried the latest one and it was quite the stinker performance wise.

I'll just link you the official forum discussion where I posted my problem. You might find those answers helpful even though I didn't. 

[http://www.regnumonline.com.ar/forum/showthread.php?t=1617&page=6](http://www.regnumonline.com.ar/forum/showthread.php?t=1617&page=6)

---

### Post by e30ernest on 2007-11-01
I have been thinking about upgrading to Gutsy but I am concerned since I heard some users having problems with the game in Gutsy.  I'd like to hear some feedback from Gutsy users.  Thanks!

---

### Post by Mayfairy on 2007-11-02
> **e30ernest said:**
> I have been thinking about upgrading to Gutsy but I am concerned since I heard some users having problems with the game in Gutsy.  I'd like to hear some feedback from Gutsy users.  Thanks!

I'm using Gutsy at the moment and can't get the game working. Not sure if it would've worked in Feisty.

---

### Post by MaximB on 2007-11-02
I had some problems in Gibbon,but eventually I got it working.
if you have problems, check the game forums Linux section ;)

---

### Post by e30ernest on 2007-11-02
> **Mayfairy said:**
> I'm using Gutsy at the moment and can't get the game working. Not sure if it would've worked in Feisty.

It works fine on Feisty (I'm using Feisty).  :)

Maxim did you experience low frame rates on Gutsy?  I heard some people had this problem.

---

### Post by MaximB on 2007-11-02
nop no problems at all, and I am using ATI.

---

### Post by Inkpot on 2007-11-09
Hi folks,

I'm running Gutsy with an ATI X1300 Pro video card with the latest restricted ATI driver enabled. When I try to run the rolauncher from the terminal, this is the output that I get:


*** glibc detected *** /home/colin/Desktop/rolauncher: double free or corruption (out): 0x08657aa0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb77e6d65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb77ea800]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb76f6961]
/home/colin/Desktop/rolauncher[0x817613d]
/home/colin/Desktop/rolauncher[0x8070b53]
/home/colin/Desktop/rolauncher[0x8065a7a]
/home/colin/Desktop/rolauncher[0x8067ed1]
/home/colin/Desktop/rolauncher[0x810074e]
/home/colin/Desktop/rolauncher[0x805c55e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7793050]
/home/colin/Desktop/rolauncher(__gxx_personality_v0+0x3d5)[0x805c391]
======= Memory map: ========
08048000-0840e000 r-xp 00000000 08:06 3957242    /home/colin/Desktop/rolauncher
0840e000-0844b000 rw-p 003c6000 08:06 3957242    /home/colin/Desktop/rolauncher
0844b000-08659000 rw-p 0844b000 00:00 0          [heap]
b6700000-b6721000 rw-p b6700000 00:00 0 
b6721000-b6800000 ---p b6721000 00:00 0 
b6893000-b691e000 r--p 00000000 08:06 3450400    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b691e000-b6920000 r-xp 00000000 08:06 3368611    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6920000-b6921000 rw-p 00001000 08:06 3368611    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6921000-b6927000 r--s 00000000 08:06 3601860    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b6927000-b692a000 r--s 00000000 08:06 3601874    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b692a000-b692e000 r--s 00000000 08:06 3601857    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b692e000-b692f000 r--s 00000000 08:06 3601867    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b692f000-b6930000 r--s 00000000 08:06 3601847    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b6930000-b6933000 r--s 00000000 08:06 3601862    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b6933000-b6934000 r--s 00000000 08:06 3601853    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b6934000-b6937000 r--s 00000000 08:06 3601851    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b6937000-b6939000 r--s 00000000 08:06 3601871    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b6939000-b6941000 r--s 00000000 08:06 3601875    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b6941000-b6947000 r--s 00000000 08:06 3601839    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b6947000-b6948000 r--s 00000000 08:06 3601845    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b6948000-b694a000 r--s 00000000 08:06 3601872    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b694a000-b6950000 r--s 00000000 08:06 3601869    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b6950000-b6954000 r--s 00000000 08:06 3601837    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b6954000-b6956000 r--s 00000000 08:06 3601893    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b6956000-b6957000 r--s 00000000 08:06 3601879    /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b6957000-b6958000 r--s 00000000 08:06 3601876    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b6958000-b6959000 r--s 00000000 08:06 3601866    /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b6959000-b695c000 r--s 00000000 08:06 3601864    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b695c000-b695f000 r--s 00000000 08:06 3601880    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b695f000-b6961000 r--s 00000000 08:06 3601836    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b6961000-b6962000 r--s 00000000 08:06 3601877    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b6962000-b6963000 r--s 00000000 08:06 3601841    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b6963000-b6964000 r--s 00000000 08:06 3601861    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b6964000-b6969000 r--s 00000000 08:06 3601856    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b6969000-b696e000 r--s 00000000 08:06 3601838    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b696e000-b6970000 r--s 00000000 08:06 3601854    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b6970000-b6973000 r--s 00000000 08:06 3601848    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b6973000-b6974000 r--s 00000000 08:06 3601873    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b6974000-b6975000 r--s 00000000 08:06 3601844    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b6975000-b6978000 r--s 00000000 08:06 3601842    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b6978000-b697e000 r--s 00000000 08:06 3601840    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b697e000-b697f000 r--s 00000000 08:06 3601858    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b697f000-b6983000 r--s 00000000 08:06 3601863    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b6983000-b6985000 r--s 00000000 08:06 3601859    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b6985000-b6989000 r--s 00000000 08:06 3601865    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b6989000-b698a000 ---p b6989000 00:00 0 
b698a000-b718a000 rwxp b698a000 00:00 0 
b718a000-b71ab000 rw-p b718a000 00:00 0 
b71ab000-b71b4000 r-xp 00000000 08:06 2780872    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b71b4000-b71b6000 rw-p 00008000 08:06 2780872    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b71b6000-b71be000 r-xp 00000000 08:06 2780874    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b71be000-b71c0000 rw-p 00007000 08:06 2780874    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b71c0000-b71d4000 r-xp 00000000 08:06 2780869    /lib/tls/i686/cmov/libnsl-2.6.1.so
b71d4000-b71d6000 rw-p 00013000 08:06 2780869    /lib/tls/i686/cmov/libnsl-2.6.1.so
b71d6000-b71d8000 rw-p b71d6000 00:00 0 
b71d8000-b71df000 r-xp 00000000 08:06 2780870    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b71df000-b71e1000 rw-p 00006000 08:06 2780870    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b71e1000-b71e4000 r--s 00000000 08:06 3601849    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b71e4000-b71eb000 r-xp 00000000 08:06 3287160    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
b71eb000-b71ec000 rw-p 00007000 08:06 3287160    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
b71ec000-b71ed000 r-xp 00000000 08:06 3238200    /usr/lib/gconv/ISO8859-1.so
b71ed000-b71ef000 rw-p 00000000 08:06 3238200    /usr/lib/gconv/ISO8859-1.so
b71ef000-b71f0000 r--p 00000000 08:06 3287962    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b71f0000-b71f1000 r--p 00000000 08:06 3287965    /usr/lib/locale/en_US.utf8/LC_TIME
b71f1000-b72d1000 r--p 00000000 08:06 3287956    /usr/lib/locale/en_US.utf8/LC_COLLATE
b72d1000-b72d2000 r--p 00000000 08:06 3287960    /usr/lib/locale/en_US.utf8/LC_MONETARY
b72d2000-b72d3000 r--p 00000000 08:06 3303146    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b72d3000-b72d4000 r--p 00000000 08:06 3287963    /usr/lib/locale/en_US.utf8/LC_PAPER
b72d4000-b72d5000 r--p 00000000 08:06 3287961    /usr/lib/locale/en_US.utf8/LC_NAME
b72d5000-b72d6000 r--p 00000000 08:06 3287955    /usr/lib/locale/en_US.utf8/LC_ADDRESS
b72d6000-b7315000 r--p 00000000 08:06 3287957    /usr/lib/locale/en_US.utf8/LC_CTYPE
b7315000-b7317000 rw-p b7315000 00:00 0 
b7317000-b7339000 r-xp 00000000 08:06 3221525    /usr/lib/libpng12.so.0.15.0
b7339000-b733a000 rw-p 00021000 08:06 3221525    /usr/lib/libpng12.so.0.15.0
b733a000-b733b000 rw-p b733a000 00:00 0 
b733b000-b73a7000 r-xp 00000000 08:06 3222880    /usr/lib/libfreetype.so.6.3.16
b73a7000-b73ab000 rw-p 0006b000 08:06 3222880    /usr/lib/libfreetype.so.6.3.16
b73ab000-b73d8000 r-xp 00000000 08:06 3223263    /usr/lib/libpangoft2-1.0.so.0.1800.2
b73d8000-b73d9000 rw-p 0002c000 08:06 3223263    /usr/lib/libpangoft2-1.0.so.0.1800.2
b73d9000-b73dd000 r-xp 00000000 08:06 3222675    /usr/lib/libXdmcp.so.6.0.0
b73dd000-b73de000 rw-p 00003000 08:06 3222675    /usr/lib/libXdmcp.so.6.0.0
b73de000-b73f3000 r-xp 00000000 08:06 3222636    /usr/lib/libICE.so.6.3.0
b73f3000-b73f5000 rw-p 00014000 08:06 3222636    /usr/lib/libICE.so.6.3.0
b73f5000-b73f7000 rw-p b73f5000 00:00 0 
b73f7000-b73f9000 r-xp 00000000 08:06 3222664    /usr/lib/libXau.so.6.0.0
b73f9000-b73fa000 rw-p 00001000 08:06 3222664    /usr/lib/libXau.so.6.0.0
b73fa000-b7402000 r-xp 00000000 08:06 3222671    /usr/lib/libXcursor.so.1.0.2
b7402000-b7403000 rw-p 00007000 08:06 3222671    /usr/lib/libXcursor.so.1.0.2
b7403000-b7408000 r-xp 00000000 08:06 3222699    /usr/lib/libXrandr.so.2.1.0
b7408000-b7409000 rw-p 00005000 08:06 3222699    /usr/lib/libXrandr.so.2.1.0
b7409000-b7410000 r-xp 00000000 08:06 3222687    /usr/lib/libXi.so.6.0.0
b7410000-b7411000 rw-p 00006000 08:06 3222687    /usr/lib/libXi.so.6.0.0
b7411000-b7418000 r-xp 00000000 08:06 3222701    /usr/lib/libXrender.so.1.3.0
b7418000-b7419000 rw-p 00006000 08:06 3222701    /usr/lib/libXrender.so.1.3.0
b7419000-b741a000 rw-p b7419000 00:00 0 
b741a000-b743d000 r-xp 00000000 08:06 3222872    /usr/lib/libfontconfig.so.1.2.0
b743d000-b7445000 rw-p 00023000 08:06 3222872    /usr/lib/libfontconfig.so.1.2.0
b7445000-b74ba000 r-xp 00000000 08:06 3222768    /usr/lib/libcairo.so.2.11.5
b74ba000-b74bc000 rw-p 00074000 08:06 3222768    /usr/lib/libcairo.so.2.11.5
b74bc000-b74bf000 r-xp 00000000 08:06 3222968    /usr/lib/libgmodule-2.0.so.0.1400.1
b74bf000-b74c0000 rw-p 00002000 08:06 3222968    /usr/lib/libgmodule-2.0.so.0.1400.1
b74c0000-b74d9000 r-xp 00000000 08:06 3222737    /usr/lib/libatk-1.0.so.0.2009.1
b74d9000-b74db000 rw-p 00018000 08:06 3222737    /usr/lib/libatk-1.0.so.0.2009.1
b74db000-b74df000 r-xp 00000000 08:06 3222681    /usr/lib/libXfixes.so.3.1.0
b74df000-b74e0000 rw-p 00003000 08:06 3222681    /usr/lib/libXfixes.so.3.1.0
b74e0000-b74e2000 r-xp 00000000 08:06 3222673    /usr/lib/libXdamage.so.1.1.0
b74e2000-b74e3000 rw-p 00001000 08:06 3222673    /usr/lib/libXdamage.so.1.1.0
b74e3000-b74e4000 rw-p b74e3000 00:00 0 
b74e4000-b74e6000 r-xp 00000000 08:06 3222669    /usr/lib/libXcomposite.so.1.0.0
b74e6000-b74e7000 rw-p 00001000 08:06 3222669    /usr/lib/libXcomposite.so.1.0.0
b74e7000-b74ef000 r-xp 00000000 08:06 3223261    /usr/lib/libpangocairo-1.0.so.0.1800.2
b74ef000-b74f0000 rw-p 00007000 08:06 3223261    /usr/lib/libpangocairo-1.0.so.0.1800.2
b74f0000-b74f7000 r-xp 00000000 08:06 2780879    /lib/tls/i686/cmov/librt-2.6.1.so
b74f7000-b74f9000 rw-p 00006000 08:06 2780879    /lib/tls/i686/cmov/librt-2.6.1.so
b74f9000-b7517000 r-xp 00000000 08:06 3222866    /usr/lib/libexpat.so.1.0.0
b7517000-b7519000 rw-p 0001e000 08:06 3222866    /usr/lib/libexpat.so.1.0.0
b7519000-b752d000 r-xp 00000000 08:06 3223442    /usr/lib/libz.so.1.2.3.3
b752d000-b752e000 rw-p 00013000 08:06 3223442    /usr/lib/libz.so.1.2.3.3
b752e000-b752f000 rw-p b752e000 00:00 0 
b752f000-b7536000 r-xp 00000000 08:06 3222654    /usr/lib/libSM.so.6.0.0
b7536000-b7537000 rw-p 00006000 08:06 3222654    /usr/lib/libSM.so.6.0.0
b7537000-b7539000 r-xp 00000000 08:06 3222689    /usr/lib/libXinerama.so.1.0.0
b7539000-b753a000 rw-p 00001000 08:06 3222689    /usr/lib/libXinerama.so.1.0.0
b753a000-b753c000 r-xp 00000000 08:06 2780866    /lib/tls/i686/cmov/libdl-2.6.1.so
b753c000-b753e000 rw-p 00001000 08:06 2780866    /lib/tls/i686/cmov/libdl-2.6.1.so
b753e000-b7578000 r-xp 00000000 08:06 3223008    /usr/lib/libgobject-2.0.so.0.1400.1
b7578000-b7579000 rw-p 0003a000 08:06 3223008    /usr/lib/libgobject-2.0.so.0.1400.1
b7579000-b7666000 r-xp 00000000 08:06 3222658    /usr/lib/libX11.so.6.2.0
b7666000-b766a000 rw-p 000ed000 08:06 3222658    /usr/lib/libX11.so.6.2.0
b766a000-b76a5000 r-xp 00000000 08:06 3223259    /usr/lib/libpango-1.0.so.0.1800.2
b76a5000-b76a7000 rw-p 0003b000 08:06 3223259    /usr/lib/libpango-1.0.so.0.1800.2
b76a7000-b76a8000 rw-p b76a7000 00:00 0 
b76a8000-b76bf000 r-xp 00000000 08:06 3222920    /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b76bf000-b76c0000 rw-p 00016000 08:06 3222920    /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b76c0000-b777c000 r-xp 00000000 08:06 3222958    /usr/lib/libglib-2.0.so.0.1400.1
b777c000-b777d000 rw-p 000bc000 08:06 3222958    /usr/lib/libglib-2.0.so.0.1400.1
b777d000-b78c1000 r-xp 00000000 08:06 2780863    /lib/tls/i686/cmov/libc-2.6.1.so
b78c1000-b78c2000 r--p 00143000 08:06 2780863    /lib/tls/i686/cmov/libc-2.6.1.so
b78c2000-b78c4000 rw-p 00144000 08:06 2780863    /lib/tls/i686/cmov/libc-2.6.1.so
b78c4000-b78c7000 rw-p b78c4000 00:00 0 
b78c7000-b78d1000 r-xp 00000000 08:06 2747203    /lib/libgcc_s.so.1
b78d1000-b78d2000 rw-p 0000a000 08:06 2747203    /lib/libgcc_s.so.1
b78d2000-b78f5000 r-xp 00000000 08:06 2780867    /lib/tls/i686/cmov/libm-2.6.1.so
b78f5000-b78f7000 rw-p 00023000 08:06 2780867    /lib/tls/i686/cmov/libm-2.6.1.so
b78f7000-b79df000 r-xp 00000000 08:06 3223372    /usr/lib/libstdc++.so.6.0.9
b79df000-b79e2000 r--p 000e8000 08:06 3223372    /usr/lib/libstdc++.so.6.0.9
b79e2000-b79e4000 rw-p 000eb000 08:06 3223372    /usr/lib/libstdc++.so.6.0.9
b79e4000-b79eb000 rw-p b79e4000 00:00 0 
b79eb000-b7a38000 r-xp 00000000 08:06 3222705    /usr/lib/libXt.so.6.0.0
b7a38000-b7a3c000 rw-p 0004c000 08:06 3222705    /usr/lib/libXt.so.6.0.0
b7a3c000-b7a49000 r-xp 00000000 08:06 3222679    /usr/lib/libXext.so.6.4.0
b7a49000-b7a4a000 rw-p 0000d000 08:06 3222679    /usr/lib/libXext.so.6.4.0
b7a4a000-b7a4e000 r-xp 00000000 08:06 3222715    /usr/lib/libXxf86vm.so.1.0.0
b7a4e000-b7a4f000 rw-p 00003000 08:06 3222715    /usr/lib/libXxf86vm.so.1.0.0
b7a4f000-b7ae7000 r-xp 00000000 08:06 3223981    /usr/lib/libGL.so.1.2
b7ae7000-b7aec000 rw-p 00098000 08:06 3223981    /usr/lib/libGL.so.1.2
b7aec000-b7aef000 rw-p b7aec000 00:00 0 
b7aef000-b7b73000 r-xp 00000000 08:06 3222918    /usr/lib/libgdk-x11-2.0.so.0.1200.0
b7b73000-b7b76000 rw-p 00084000 08:06 3222918    /usr/lib/libgdk-x11-2.0.so.0.1200.0
b7b76000-b7ef3000 r-xp 00000000 08:06 3223073    /usr/lib/libgtk-x11-2.0.so.0.1200.0
b7ef3000-b7efa000 rw-p 0037c000 08:06 3223073    /usr/lib/libgtk-x11-2.0.so.0.1200.0
b7efa000-b7efc000 rw-p b7efa000 00:00 0 
b7efc000-b7f00000 r-xp 00000000 08:06 3223070    /usr/lib/libgthread-2.0.so.0.1400.1
b7f00000-b7f01000 rw-p 00003000 08:06 3223070    /usr/lib/libgthread-2.0.so.0.1400.1
b7f01000-b7f15000 r-xp 00000000 08:06 2780877    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7f15000-b7f17000 rw-p 00013000 08:06 2780877    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7f17000-b7f19000 rw-p b7f17000 00:00 0 
b7f19000-b7f1a000 r--p 00000000 08:06 3287964    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7f1a000-b7f1b000 r--p 00000000 08:06 3287959    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7f1b000-b7f1c000 r--p 00000000 08:06 3287958    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7f1c000-b7f1e000 r-xp 00000000 08:06 3238255    /usr/lib/gconv/UTF-32.so
b7f1e000-b7f20000 rw-p 00001000 08:06 3238255    /usr/lib/gconv/UTF-32.so
b7f20000-b7f27000 r--s 00000000 08:06 3238259    /usr/lib/gconv/gconv-modules.cache
b7f27000-b7f29000 rw-p b7f27000 00:00 0 
b7f29000-b7f43000 r-xp 00000000 08:06 2747357    /lib/ld-2.6.1.so
b7f43000-b7f45000 rw-p 00019000 08:06 2747357    /lib/ld-2.6.1.so
bffdb000-bffef000 rwxp bffdb000 00:00 0          [stack]
bffef000-bfff1000 rw-p bffef000 00:00 0 
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)


I've searched on these forums and the official Regnum forums, but can't find any solution. Can anyone help?


Inkpot

---

### Post by queso_lg on 2007-11-22
Hi people.. i recentrly installed ubuntu Gutsy Gibbon 7,10 on my computer and i come from XP!!!.. i been trying to install Regnum for about 2 days now reading every post that i found.. this was the closest one to get it working. After i did a sudo dpkg-reconfigure -phigh xserver-xorg.. i found a new error:

b7f93000-b7fad000 r-xp 00000000 03:02 750721 /lib/ld-2.6.1.so
b7fad000-b7faf000 rw-p 00019000 03:02 750721 /lib/ld-2.6.1.so
bfb67000-bfb7b000 rwxp bfb67000 00:00 0 [stack]
bfb7b000-bfb7d000 rw-p bfb7b000 00:00 0
ffffe000-fffff000 r-xp 00000000 00:00 0 [vdso]
Cancelado (core dumped)

this is where it stops... any suggestions?? please!!

---

### Post by csi_ on 2007-12-31
> **alecto said:**
> I had a quick search on google and it seems that you can simply fire up 'driconf' in a terminal and enable S3TC support from there. In the Image Quality tab I ticked the "Enable S3TC..." box and changed it to 'Yes' and now the game loads!

However!... Upon successfully loading I get an error message saying it couldn't connect to the server. I assume this is to do with my connection being blocked by my university or perhaps the server's down..

Well, I managed to bypass *driconf* modification, and get really _good results_ on Regnum Online with radeon driver. (I had strange texture rendering with driconf modification) 

My card is: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

To get it working, 
[INDENT]1. get working direct rendering, (see prevoious posts)
2. install *libtxc-dxtn_070518-0m2k1_i386.deb* from  [http://madman2k.net](http://madman2k.net)[/INDENT]

et voilà!

---

### Post by dannyboy79 on 2007-12-31
I am joining the ubuntu clan within Alyius (or however you spell it). I am at the part where I can select to add 5 points to any attribute, do you ahve any sugestions or did I read that I shouldn't hit the plus (+) symbol?
i chose a warrior uthgar

---

### Post by Hightide on 2007-12-31
yes, my sister plays Regnum and loves it

great game by the Argentinian dudes :)

---

### Post by nille on 2008-01-01
> **Inkpot said:**
> Hi folks,

I'm running Gutsy with an ATI X1300 Pro video card with the latest restricted ATI driver enabled. When I try to run the rolauncher from the terminal, this is the output that I get:


*** glibc detected *** /home/colin/Desktop/rolauncher: double free or corruption (out): 0x08657aa0 ***
[...]
Aborted (core dumped)


I've searched on these forums and the official Regnum forums, but can't find any solution. Can anyone help?


Inkpot

That problem could be solved by starting rolauncher with MALLOC_CHECK_=0 like this:

**MALLOC_CHECK_=0 ./rolauncher**

Try it, and if it doesn't work, check one of these threads:
[http://www.regnumonline.com.ar/forum/showthread.php?t=10618](http://www.regnumonline.com.ar/forum/showthread.php?t=10618)
[http://www.regnumonline.com.ar/forum/showthread.php?t=17271](http://www.regnumonline.com.ar/forum/showthread.php?t=17271)
[http://www.regnumonline.com.ar/forum/showthread.php?t=16679](http://www.regnumonline.com.ar/forum/showthread.php?t=16679)
[http://www.regnumonline.com.ar/forum/showthread.php?t=14566](http://www.regnumonline.com.ar/forum/showthread.php?t=14566)

---

### Post by nille on 2008-01-18
Seems like there's a problem with the latest xserver-xorg-core update (2:1.3.0.0.dfsg-12ubuntu8.1), and it stops rolauncher from starting.

Check out this thread:
[http://www.regnumonline.com.ar/forum/showthread.php?t=18025](http://www.regnumonline.com.ar/forum/showthread.php?t=18025)

---

### Post by KhaaL on 2008-01-18
Oh, piffle... I was eager to test this game out when this bug came in the way and stopped me :(

---

### Post by dannyboy79 on 2008-01-18
i guess I am glad my main server/computer is still running feisty then. can't you just install the previous xserver-xorg-core package and lock it so it doesn't update? I am pretty sure aptitude and or apt-get can do this.

---

### Post by MaximB on 2008-01-18
I have Gibbon and first I had problems but after I run this command : MALLOC_CHECK_=0 ./rolauncher , or something similar I have no problems at all.
So upgrading a distro shouldn't be a problem for Regnum Online.

---

### Post by KhaaL on 2008-01-18
That command does not help me, I'm on Gutsy.

@dannyboy: I think that's possible, but the package is installed already now and I don't even know how much trouble this game is worth :) I'll wait til' they fix it...

---

### Post by nille on 2008-01-18
It's a bug in the latest xserver-xorg-core package (2:1.3.0.0.dfsg-12ubuntu8.1), but you will do fine with the older version until they release a fix. To downgrade, if you have already upgraded, you can do this:
```
sudo apt-get install xserver-xorg-core=2:1.3.0.0.dfsg-12ubuntu8
```

The bug is here:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969)

**EDIT:** Bug is temporarily fixed due to version *8.2

---

### Post by Frazer on 2008-04-11
Iv been playing a few days now and quite like this game, im a lvl 17 Hunter in Syrtis called Exequiel.

Unless its picking a class like Hunter or Markman ect any skill points can be changed

/reset_powers

and you can respec the skillpoints

---

### Post by Adrian_b on 2008-04-15
I don't really know how to install this.
I've followed all the instructions but it keeps on doing something wrong but I've got no idea what it's doing wrong exactly.
Any help with this please? :)


```
sagara@sousuke:~$ mkdir regnum
sagara@sousuke:~$ cd regnum
sagara@sousuke:~/regnum$ wget http://www.regnumonline.com.ar/downloads/files/rolauncher.tar.gz
--18:24:05--  http://www.regnumonline.com.ar/downloads/files/rolauncher.tar.gz
           => `rolauncher.tar.gz'
Resolving www.regnumonline.com.ar... 212.214.41.26
Connecting to www.regnumonline.com.ar|212.214.41.26|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,824,196 (1.7M) [application/x-tar]

100%[============================================================================>] 1,824,196    228.79K/s    ETA 00:00

18:24:11 (287.06 KB/s) - `rolauncher.tar.gz' saved [1824196/1824196]

sagara@sousuke:~/regnum$ tar xfz rolauncher.tar.gz
sagara@sousuke:~/regnum$ rm rolauncher.tar.gz
sagara@sousuke:~/regnum$ chmod +x rolauncher
sagara@sousuke:~/regnum$ ./rolauncher

(rolauncher:10777): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
*** glibc detected *** ./rolauncher: double free or corruption (out): 0x0867b2a0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7868d65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb786c800]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb7778961]
./rolauncher[0x817613d]
./rolauncher[0x8070b53]
./rolauncher[0x8065a7a]
./rolauncher[0x8067ed1]
./rolauncher[0x810074e]
./rolauncher[0x805c55e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7815050]
./rolauncher(__gxx_personality_v0+0x3d5)[0x805c391]
======= Memory map: ========
08048000-0840e000 r-xp 00000000 03:41 147651     /home/sagara/regnum/rolauncher
0840e000-0844b000 rw-p 003c6000 03:41 147651     /home/sagara/regnum/rolauncher
0844b000-08680000 rw-p 0844b000 00:00 0          [heap]
b5e00000-b5e21000 rw-p b5e00000 00:00 0 
b5e21000-b5f00000 ---p b5e21000 00:00 0 
b5f0a000-b5f86000 r--p 00000000 03:41 523817     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansCondensed.ttf
b5f86000-b5f88000 r-xp 00000000 03:41 408818     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5f88000-b5f89000 rw-p 00001000 03:41 408818     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5f89000-b5f8f000 r--s 00000000 03:41 608711     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b5f8f000-b5f90000 r--s 00000000 03:41 608442     /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b5f90000-b5f92000 r--s 00000000 03:41 608441     /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b5f92000-b5f93000 r--s 00000000 03:41 608440     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b5f93000-b5f94000 r--s 00000000 03:41 608439     /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b5f94000-b5f98000 r--s 00000000 03:41 608438     /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b5f98000-b5f99000 r--s 00000000 03:41 608437     /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b5f99000-b5f9c000 r--s 00000000 03:41 608436     /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-x86.cache-2
b5f9c000-b5f9d000 r--s 00000000 03:41 608435     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b5f9d000-b5f9f000 r--s 00000000 03:41 608434     /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b5f9f000-b5fa2000 r--s 00000000 03:41 608433     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b5fa2000-b5fa4000 r--s 00000000 03:41 608432     /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b5fa4000-b5fa5000 r--s 00000000 03:41 608431     /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b5fa5000-b5fa7000 r--s 00000000 03:41 608430     /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b5fa7000-b5fad000 r--s 00000000 03:41 608429     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b5fad000-b5faf000 r--s 00000000 03:41 608428     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b5faf000-b5fb1000 r--s 00000000 03:41 608427     /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b5fb1000-b5fb7000 r--s 00000000 03:41 608426     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b5fb7000-b5fb8000 r--s 00000000 03:41 608425     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b5fb8000-b5fcf000 r--s 00000000 03:41 609986     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b5fcf000-b5fd5000 r--s 00000000 03:41 608424     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b5fd5000-b5fdc000 r--s 00000000 03:41 608053     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b5fdc000-b5fdd000 r--s 00000000 03:41 608788     /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b5fdd000-b5fde000 r--s 00000000 03:41 608787     /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b5fde000-b5fdf000 r--s 00000000 03:41 609998     /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86.cache-2
b5fdf000-b5fe1000 r--s 00000000 03:41 610123     /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b5fe1000-b5fe4000 r--s 00000000 03:41 608784     /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b5fe4000-b5fec000 r--s 00000000 03:41 610038     /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b5fec000-b5fee000 r--s 00000000 03:41 610005     /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b5fee000-b5ff0000 r--s 00000000 03:41 610026     /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b5ff0000-b5ff5000 r--s 00000000 03:41 608779     /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b5ff5000-b5ff9000 r--s 00000000 03:41 610024     /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b5ff9000-b5ffb000 r--s 00000000 03:41 608777     /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b5ffb000-b5ffc000 r--s 00000000 03:41 610004     /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b5ffc000-b5ffd000 r--s 00000000 03:41 610036     /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86.cache-2
b5ffd000-b6001000 r--s 00000000 03:41 610034     /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b6001000-b6007000 r--s 00000000 03:41 608718     /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b6007000-b600d000 r--s 00000000 03:41 609965     /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b600d000-b6033000 r-xp 00000000 03:41 327176     /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6033000-b6034000 rw-p 00025000 03:41 327176     /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6034000-b6035000 ---p b6034000 00:00 0 
b6035000-b6835000 rwxp b6035000 00:00 0 
b6835000-b683e000 r-xp 00000000 03:41 426188     /lib/tls/i686/cmov/libnss_files-2.6.1.so
b683e000-b6840000 rw-p 00008000 03:41 426188     /lib/tls/i686/cmov/libnss_files-2.6.1.so
b6840000-b6848000 r-xp 00000000 03:41 426190     /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b6848000-b684a000 rw-p 00007000 03:41 426190     /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b684a000-b685e000 r-xp 00000000 03:41 426185     /lib/tls/i686/cmov/libnsl-2.6.1.so
b685e000-b6860000 rw-p 00013000 03:41 426185     /lib/tls/i686/cmov/libnsl-2.6.1.so
b6860000-b6862000 rw-p b6860000 00:00 0 
b6862000-b6869000 r-xp 00000000 03:41 426186     /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b6869000-b686b000 rw-p 00006000 03:41 426186     /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b686b000-b686f000 r--s 00000000 03:41 610033     /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b686f000-b6871000 r--s 00000000 03:41 610002     /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b6871000-b6875000 r--s 00000000 03:41 610030     /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b6875000-b6876000 r-xp 00000000 03:41 268257     /usr/lib/gconv/ISO8859-1.so
b6876000-b6878000 rw-p 00000000 03:41 268257     /usr/lib/gconv/ISO8859-1.so
b6878000-b6958000 r--p 00000000 03:41 363203     /usr/lib/locale/en_US.utf8/LC_COLLATE
b6958000-b695a000 r-xp 00000000 03:41 268312     /usr/lib/gconv/UTF-32.so
b695a000-b695c000 rw-p 00001000 03:41 268312     /usr/lib/gconv/UTF-32.so
b695c000-b6963000 r--s 00000000 03:41 261775     /usr/lib/gconv/gconv-modules.cache
b6963000-b69a2000 r--p 00000000 03:41 363204     /usr/lib/locale/en_US.utf8/LC_CTYPE
b69a2000-b69ff000 rw-p b69a2000 00:00 0 
b69ff000-b6a21000 r-xp 00000000 03:41 262764     /usr/lib/libpng12.so.0.15.0
b6a21000-b6a22000 rw-p 00021000 03:41 262764     /usr/lib/libpng12.so.0.15.0
b6a22000-b6a8e000 r-xp 00000000 03:41 263682     /usr/lib/libfreetype.so.6.3.16
b6a8e000-b6a92000 rw-p 0006b000 03:41 263682     /usr/lib/libfreetype.so.6.3.16
b6a92000-b6abf000 r-xp 00000000 03:41 265176     /usr/lib/libpangoft2-1.0.so.0.1800.3
b6abf000-b6ac0000 rw-p 0002c000 03:41 265176     /usr/lib/libpangoft2-1.0.so.0.1800.3
b6ac0000-b6ac1000 rw-p b6ac0000 00:00 0 
b6ac1000-b6ac5000 r-xp 00000000 03:41 263400     /usr/lib/libXdmcp.so.6.0.0
b6ac5000-b6ac6000 rw-p 00003000 03:41 263400     /usr/lib/libXdmcp.so.6.0.0
b6ac6000-b6adb000 r-xp 00000000 03:41 263353     /usr/lib/libICE.so.6.3.0
b6adb000-b6add000 rw-p 00014000 03:41 263353     /usr/lib/libICE.so.6.3.0
b6add000-b6ade000 rw-p b6add000 00:00 0 
b6ade000-b6ae0000 r-xp 00000000 03:41 263389     /usr/lib/libXau.so.6.0.0
b6ae0000-b6ae1000 rw-p 00001000 03:41 263389     /usr/lib/libXau.so.6.0.0
b6ae1000-b6ae2000 r-xp 00000000 03:41 343500     /usr/lib/tls/libnvidia-tls.so.100.14.19
b6ae2000-b6ae3000 rw-p 00000000 03:41 343500     /usr/lib/tls/libnvidia-tls.so.100.14.19
b6ae3000-b6ae4000 rw-p b6ae3000 00:00 0 
b6ae4000-b7440000 r-xp 00000000 03:41 262863     /usr/lib/libGLcore.so.100.14.19
b7440000-b7478000 rwxp 0095c000 03:41 262863     /usr/lib/libGLcore.so.100.14.19
b7478000-b747c000 rwxp b7478000 00:00 0 
b747c000-b7484000 r-xp 00000000 03:41 263396     /usr/lib/libXcursor.so.1.0.2
b7484000-b7485000 rw-p 00007000 03:41 263396     /usr/lib/libXcursor.so.1.0.2
b7485000-b748a000 r-xp 00000000 03:41 263424     /usr/lib/libXrandr.so.2.1.0
b748a000-b748b000 rw-p 00005000 03:41 263424     /usr/lib/libXrandr.so.2.1.0
b748b000-b7492000 r-xp 00000000 03:41 263412     /usr/lib/libXi.so.6.0.0
b7492000-b7493000 rw-p 00006000 03:41 263412     /usr/lib/libXi.so.6.0.0
b7493000-b749a000 r-xp 00000000 03:41 263426     /usr/lib/libXrender.so.1.3.0
b749a000-b749b000 rw-p 00006000 03:41 263426     /usr/lib/libXrender.so.1.3.0
b749b000-b749c000 rw-p b749b000 00:00 0 
b749c000-b74bf000 r-xp 00000000 03:41 263672     /usr/lib/libfontconfig.so.1.2.0
b74bf000-b74c7000 rw-p 00023000 03:41 263672     /usr/lib/libfontconfig.so.1.2.0
b74c7000-b753c000 r-xp 00000000 03:41 261772     /usr/lib/libcairo.so.2.11.5
b753c000-b753e000 rw-p 00074000 03:41 261772     /usr/lib/libcairo.so.2.11.5
b753e000-b7541000 r-xp 00000000 03:41 263788     /usr/lib/libgmodule-2.0.so.0.1400.1
b7541000-b7542000 rw-p 00002000 03:41 263788     /usr/lib/libgmodule-2.0.so.0.1400.1
b7542000-b755b000 r-xp 00000000 03:41 263495     /usr/lib/libatk-1.0.so.0.2009.1
b755b000-b755d000 rw-p 00018000 03:41 263495     /usr/lib/libatk-1.0.so.0.2009.1
b755d000-b7561000 r-xp 00000000 03:41 263406     /usr/lib/libXfixes.so.3.1.0
b7561000-b7562000 rw-p 00003000 03:41 263406     /usr/lib/libXfixes.so.3.1.0
b7562000-b7564000 r-xp 00000000 03:41 263398     /usr/lib/libXdamage.so.1.1.0
b7564000-b7565000 rw-p 00001000 03:41 263398     /usr/lib/libXdamage.so.1.1.0
b7565000-b7566000 rw-p b7565000 00:00 0 
b7566000-b7568000 r-xp 00000000 03:41 263394     /usr/lib/libXcomposite.so.1.0.0
b7568000-b7569000 rw-p 00001000 03:41 263394     /usr/lib/libXcomposite.so.1.0.0
b7569000-b7571000 r-xp 00000000 03:41 263625     /usr/lib/libpangocairo-1.0.so.0.1800.3
b7571000-b7572000 rw-p 00007000 03:41 263625     /usr/lib/libpangocairo-1.0.so.0.1800.3
b7572000-b7579000 r-xp 00000000 03:41 426195     /lib/tls/i686/cmov/librt-2.6.1.so
b7579000-b757b000 rw-p 00006000 03:41 426195     /lib/tls/i686/cmov/librt-2.6.1.so
b757b000-b7599000 r-xp 00000000 03:41 263652     /usr/lib/libexpat.so.1.0.0
b7599000-b759b000 rw-p 0001e000 03:41 263652     /usr/lib/libexpat.so.1.0.0
b759b000-b75af000 r-xp 00000000 03:41 264510     /usr/lib/libz.so.1.2.3.3
b75af000-b75b0000 rw-p 00013000 03:41 264510     /usr/lib/libz.so.1.2.3.3
b75b0000-b75b1000 rw-p b75b0000 00:00 0 
b75b1000-b75b8000 r-xp 00000000 03:41 263377     /usr/lib/libSM.so.6.0.0
b75b8000-b75b9000 rw-p 00006000 03:41 263377     /usr/lib/libSM.so.6.0.0
b75b9000-b75bb000 r-xp 00000000 03:41 263414     /usr/lib/libXinerama.so.1.0.0
b75bb000-b75bc000 rw-p 00001000 03:41 263414     /usr/lib/libXinerama.so.1.0.0
b75bc000-b75be000 r-xp 00000000 03:41 426182     /lib/tls/i686/cmov/libdl-2.6.1.so
b75be000-b75c0000 rw-p 00001000 03:41 426182     /lib/tls/i686/cmov/libdl-2.6.1.so
b75c0000-b75fa000 r-xp 00000000 03:41 263830     /usr/lib/libgobject-2.0.so.0.1400.1
b75fa000-b75fb000 rw-p 0003a000 03:41 263830     /usr/lib/libgobject-2.0.so.0.1400.1
b75fb000-b76e8000 r-xp 00000000 03:41 263383     /usr/lib/libX11.so.6.2.0
b76e8000-b76ec000 rw-p 000ed000 03:41 263383     /usr/lib/libX11.so.6.2.0
b76ec000-b7727000 r-xp 00000000 03:41 263617     /usr/lib/libpango-1.0.so.0.1800.3
b7727000-b7729000 rw-p 0003b000 03:41 263617     /usr/lib/libpango-1.0.so.0.1800.3
b7729000-b772a000 rw-p b7729000 00:00 0 
b772a000-b7741000 r-xp 00000000 03:41 263723     /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b7741000-b7742000 rw-p 00016000 03:41 263723     /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b7742000-b77fe000 r-xp 00000000 03:41 263778     /usr/lib/libglib-2.0.so.0.1400.1
b77fe000-b77ff000 rw-p 000bc000 03:41 263778     /usr/lib/libglib-2.0.so.0.1400.1
b77ff000-b7943000 r-xp 00000000 03:41 426179     /lib/tls/i686/cmov/libc-2.6.1.so
b7943000-b7944000 r--p 00143000 03:41 426179     /lib/tls/i686/cmov/libc-2.6.1.so
b7944000-b7946000 rw-p 00144000 03:41 426179     /lib/tls/i686/cmov/libc-2.6.1.so
b7946000-b7949000 rw-p b7946000 00:00 0 
b7949000-b7953000 r-xp 00000000 03:41 392517     /lib/libgcc_s.so.1
b7953000-b7954000 rw-p 0000a000 03:41 392517     /lib/libgcc_s.so.1
b7954000-b7977000 r-xp 00000000 03:41 426183     /lib/tls/i686/cmov/libm-2.6.1.so
b7977000-b7979000 rw-p 00023000 03:41 426183     /lib/tls/i686/cmov/libm-2.6.1.so
b7979000-b7a61000 r-xp 00000000 03:41 264371     /usr/lib/libstdc++.so.6.0.9
b7a61000-b7a64000 r--p 000e8000 03:41 264371     /usr/lib/libstdc++.so.6.0.9
b7a64000-b7a66000 rw-p 000eb000 03:41 264371     /usr/lib/libstdc++.so.6.0.9
b7a66000-b7a6d000 rw-p b7a66000 00:00 0 
b7a6d000-b7aba000 r-xp 00000000 03:41 263430     /usr/lib/libXt.so.6.0.0
b7aba000-b7abe000 rw-p 0004c000 03:41 263430     /usr/lib/libXt.so.6.0.0
b7abe000-b7acb000 r-xp 00000000 03:41 263404     /usr/lib/libXext.so.6.4.0
b7acb000-b7acc000 rw-p 0000d000 03:41 263404     /usr/lib/libXext.so.6.4.0
b7acc000-b7ad0000 r-xp 00000000 03:41 263444     /usr/lib/libXxf86vm.so.1.0.0
b7ad0000-b7ad1000 rw-p 00003000 03:41 263444     /usr/lib/libXxf86vm.so.1.0.0
b7ad1000-b7b4b000 r-xp 00000000 03:41 262835     /usr/lib/libGL.so.100.14.19
b7b4b000-b7b66000 rwxp 00079000 03:41 262835     /usr/lib/libGL.so.100.14.19
b7b66000-b7b67000 rwxp b7b66000 00:00 0 
b7b67000-b7beb000 r-xp 00000000 03:41 263721     /usr/lib/libgdk-x11-2.0.so.0.1200.0
b7beb000-b7bee000 rw-p 00084000 03:41 263721     /usr/lib/libgdk-x11-2.0.so.0.1200.0
b7bee000-b7f6b000 r-xp 00000000 03:41 263892     /usr/lib/libgtk-x11-2.0.so.0.1200.0
b7f6b000-b7f72000 rw-p 0037c000 03:41 263892     /usr/lib/libgtk-x11-2.0.so.0.1200.0
b7f72000-b7f74000 rw-p b7f72000 00:00 0 
b7f74000-b7f78000 r-xp 00000000 03:41 263890     /usr/lib/libgthread-2.0.so.0.1400.1
b7f78000-b7f79000 rw-p 00003000 03:41 263890     /usr/lib/libgthread-2.0.so.0.1400.1
b7f79000-b7f8d000 r-xp 00000000 03:41 426193     /lib/tls/i686/cmov/libpthread-2.6.1.so
b7f8d000-b7f8f000 rw-p 00013000 03:41 426193     /lib/tls/i686/cmov/libpthread-2.6.1.so
b7f8f000-b7f91000 rw-p b7f8f000 00:00 0 
b7f91000-b7f92000 r--s 00000000 03:41 121104     /home/sagara/.fontconfig/918dd5c8ed793dbdac05e26d7d157912-x86.cache-2
b7f92000-b7f93000 r--p 00000000 03:41 363209     /usr/lib/locale/en_US.utf8/LC_NUMERIC
b7f93000-b7f94000 r--p 00000000 03:41 363212     /usr/lib/locale/en_US.utf8/LC_TIME
b7f94000-b7f95000 r--p 00000000 03:41 363207     /usr/lib/locale/en_US.utf8/LC_MONETARY
b7f95000-b7f96000 r--p 00000000 03:41 363213     /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f96000-b7f97000 r--p 00000000 03:41 363210     /usr/lib/locale/en_US.utf8/LC_PAPER
b7f97000-b7f98000 r--p 00000000 03:41 363208     /usr/lib/locale/en_US.utf8/LC_NAME
b7f98000-b7f99000 r--p 00000000 03:41 363202     /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7f99000-b7f9a000 r--p 00000000 03:41 363211     /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7f9a000-b7f9b000 r--p 00000000 03:41 363206     /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7f9b000-b7f9c000 r--p 00000000 03:41 363205     /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7f9c000-b7f9e000 rwxp 00000000 00:0e 2741       /dev/zero
b7f9e000-b7fa0000 rw-p b7f9e000 00:00 0 
b7fa0000-b7fba000 r-xp 00000000 03:41 393017     /lib/ld-2.6.1.so
b7fba000-b7fbc000 rw-p 00019000 03:41 393017     /lib/ld-2.6.1.so
bfe7e000-bfe93000 rwxp bfe7e000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)
sagara@sousuke:~/regnum$ 


```

---

### Post by nille on 2008-04-16
You get the "double free of corruption"-error, so instead of running **./rolauncher** you can try this:

**MALLOC_CHECK_=0 ./rolauncher**

Or, perhaps:

**MALLOC_CHECK_=1 ./rolauncher**

This is probably needed only the first time you run it.

---

### Post by Adrian_b on 2008-04-17
> **nille said:**
> You get the "double free of corruption"-error, so instead of running **./rolauncher** you can try this:

**MALLOC_CHECK_=0 ./rolauncher**

Or, perhaps:

**MALLOC_CHECK_=1 ./rolauncher**

This is probably needed only the first time you run it.


Thanks, that worked perfectly.
I'm having some crashes here and there though, including full X crashes.
But I can live with that for the moment :)

---

