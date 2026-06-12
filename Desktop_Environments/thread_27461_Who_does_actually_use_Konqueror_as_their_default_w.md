---
title: "Who does actually use Konqueror as their default web browser ?"
date: 2005-04-16
forum: Desktop Environments
---

### Post by kal_zakath on 2005-04-16
Well, all is in the title  :) 

I'd like to go full KDE and I decided to try to use only konqueror as my web browser. But many people does think that Konqueror is not ready yet to be a good web browser. I'm writing this post from Konqueror and I didn't noticed any problem yet but I don't know if it will last forever...

If you have exemples of websites that don't work with konqueror, please post it here, I'd like to test it.

---

### Post by Terracotta on 2005-04-16
I most certainly do,

though I am a noob I'ld say it rocks,
I used firefox in windows, wich is a very good browser, it does open the sites konqueror doesn't render well, but the improvements that have been made in konqueror are clear (in the K.U.L they still use kde 3.2 and there I regularly have to open mozilla because konqueror doesn't render sites right), but to me since kde 3.3 it looks like it is ready as a browser, the moment I started with mepis 3.3 wich has kde 3.3, I rarely use firefox, because it isn't necessary anymore :-).

sites that doesn't render well:
[www.letssingit.com](www.letssingit.com) (only on the top where you have to right the searche command isn't enough space to show everything, but you can scroll it :s)

other sites are welcome ;-),

Oh, one more thing, I found that if you write a polite e-mail to the webmasters, they sometimes give a nice replye that they'll take care of the problem.

---

### Post by Manny C on 2005-04-16
Hi 

How many of you actually use Gmail? I do...konqueror isn't supported and hence I use firefox by default.

---

### Post by tristure on 2005-04-16
Konqueror is a very good browser.

If you use Kde I think it's a good choice to use it as the default browser.

Compared with firefox : it's faster (loading and rendering), and on most site the rendering quality is as good as firefox.

Now Konqueror does have problems with some sites, so it is a good idea to keep firefox installed as well.

An example : [www.allmusic.com](www.allmusic.com)

---

### Post by kal_zakath on 2005-04-16
@Manny C : Huh ? I just tried Gmail after reading you message, and it works just fine  :) 

EDIT : hoo, I see what you mean, it isn't a fully supported browser... that's quite annoying, you're true, but not really a problem for me as I use gmail with POP.


@Terracotta : thanks for the website, as long as it is only little annoyances like that it is still possible to use konqueror. As long as I do not find any website that is unusable with konkeror I think I'll stick with it.

@ tristure : hmm, strange, yhe website you give works just fine  :-?

---

### Post by denzilla on 2005-04-16
I wish they would kill konqueror and make a "K' version of Firefox. Konqueror will never be mainstream enough to get full support.

---

### Post by Terracotta on 2005-04-16
Not completely true, since KHTML is now used by apple's browser safari, it has more support and you really can see the differences from the moment that happened, I rarely enter a site wich doesn't render. I'ld say, keep up the good work.
And there's one more reason that a variety in browsers is a good thing: the more people use different kinds of browsers, the more webmaster have to stick to the standards wich will cause better rendering in any browser.

---

### Post by deadlands on 2005-04-16
Konqueror is too slow on my system. It takes it awhile to find the site in DNS and then load it. Firefox just loads sites right up. (anyone have a clue why Konqueror would be so slow?)

I like Konqueror, but I use Firefox because of the extensions and Gmail support.

---

### Post by aramazan on 2005-04-16
[QUOTE=deadlands]Konqueror is too slow on my system. It takes it awhile to find the site in DNS and then load it. Firefox just loads sites right up. (anyone have a clue why Konqueror would be so slow?)[/QUOTE]
1. To boost Konqueror web browsing speed:
sudo echo "KDE_NO_IPV6=true" >> /etc/environment
(Also someone has reported that he was occasionally experiencing Konqueror crashes, but they've dissapeared after "KDE_NO_IPV6=true")

2. I only use Konqueror for web browsing but usually I also install Firefox along with Konq, because they have different engines so if a site has JScript or rendering issues in one browser, it would usually work OK in the other. That said, currently I've got only Konqueror installed on this Kubuntu 5.04 machine (a week passed and still waiting for a problematic site to bother with installing Firefox).

3. Because of [2] I can't give you precise memory consumption figures of Konqueror vs. Firefox. But I had once noted them for a variety of browsers posted it at [http://groups.google.com/groups?selm=2v78ftF2htch4U1@uni-berlin.de](http://groups.google.com/groups?selm=2v78ftF2htch4U1@uni-berlin.de)

Here is the excerpt:
> I had said that running Konqueror on KDE gives it an advantage of using KDE and Qt libraries that are already loaded. So I've done another test, this time on GNOME, to see the memory foot print of all the alternatives. Again, all of them displaying the same URL, with no multiple tabs.
(Got them via "ps axlw | less" --> VSZ columns of relevant binaries)

Konqueror: 38264K
Opera    : 59920K
Firefox  : 86011K
Mozilla  : 92260K
Epiphany : 93116K

---

### Post by deadlands on 2005-04-16
[QUOTE=aramazan]1. To boost Konqueror web browsing speed:
sudo echo "KDE_NO_IPV6=true" >> /etc/environment
(Also someone has reported that he was occasionally experiencing Konqueror crashes, but they've dissapeared after "KDE_NO_IPV6=true")[/quote]

Thank you! For some reason I was getting permission denied, but I just edited the file to add that line. 

This forum is so helpful, I'm glad I decided to give Kubuntu a whirl.

---

### Post by aramazan on 2005-04-17
[QUOTE=deadlands]Thank you! For some reason I was getting permission denied, but I just edited the file to add that line.[/QUOTE]You're welcome :)
BTW, I've submitted bug#9833 to bugzilla  for sudo permission issue.

---

### Post by Terracotta on 2005-04-17
wouldn't it be nice to set up a poll for this ;-), to see how many actually install another browser in kubuntu, and use that as their default, or as second browser?

---

### Post by kal_zakath on 2005-04-17
Yeah, I thought about  a poll after I did post this topic, but I now it's too late, I can't add a poll afterwards. Maybe a moderator can do that ?

---

### Post by kal_zakath on 2005-04-17
I found somthing quite funny : the konqueror official website doesn't render well in.....konqueror  ](*,) 

Try this page : [http://www.konqueror.org/features/browser.php](http://www.konqueror.org/features/browser.php)

and reload it a few times, you'll notice that there is a problem with tha "waves" at the bottom and the text witch is on the same layer.

Funny isn't it ? But it doesn't look really "professional" [-X 

Maybe I'll drop them a mail to show them the problem, with screenshots.   :roll:

---

### Post by F for Fragging on 2005-04-17
Yes, I've also seen it. Quite ironical that the Konqueror website doesn't render correctly in Konqueror.

I use Konqueror as my main browser as well. Somehow it seems to me that it is quite slow, a lot slower than Firefox. Another one of my problems is that it uses the font that I use for KDE for certain websites (for example dot.kde.org, which looks fine under Windows with Firefox). It might be a wrong setting in my KDE Control Center somewhere, but it's annoying. Also if I read articles on wikipedia the font size is so huge, in Firefox the font size is correct if I acess wikipedia articles.

Konqueror needs some more work, but it's already usable for me as default webbrowser. I like how everything is integrated in Konqueror, and that I can also use it as a file manager and for FTP acess.

---

### Post by dermotti on 2005-04-17
Wow thats messed up.


I wish i could use konqueror,, cuz for most things its faster than firefox. But it just doesnt work with alot of the site si use, especialy financial ones like online banks and such,.

---

### Post by deadlands on 2005-04-17
[QUOTE=aramazan]You're welcome :)
BTW, I've submitted bug#9833 to bugzilla  for sudo permission issue.[/QUOTE]

BTW, that fixed worked great. Now that I remember, disabling IPv6 is one of the ways to get Firefox to speed up.

---

### Post by !nkubus on 2005-04-17
One of the main reasons i use Firefox is the mouse gestures exentions, and the fact that konqueror does not have them ... well i know i could get them with khotkeys but khotkeys crash when you opnen's it ;)

---

### Post by deadlands on 2005-04-17
[QUOTE=!nkubus]One of the main reasons i use Firefox is the mouse gestures exentions, and the fact that konqueror does not have them ... well i know i could get them with khotkeys but khotkeys crash when you opnen's it ;)[/QUOTE]

There are a few extensions that keep me from not using Firefox, like Session Saver, Gmail Notifier and Allow Right-Click.

Also, complete Gmail support is important to me.

---

### Post by lerrup on 2005-04-17
well, as I can only listen to the beeb in Konq and not firefox, me.

And I like it.

---

### Post by nautilus on 2005-04-17
It's somewhat odd to see this discussion... I've used Konqueror as my only web-browser for, hmm, a year or so?

I've never had a problem with compatibility, and as for rendering issues I doubt it's fair to tackle the browser as the culprit straight off, especially the sites mentioned; frankly the HTML looks atrocious.

But, that said, Konqueror has many features which make it stand far above Firefox, at least on my Ubuntu desktop, such as extremely fast loading, spell checking (which I conveniently ignore frequently), TTS, session resuming, and tabs which don't scroll off your tab-bar after 6 or something silly like that.

Oh hello, I don't even have firefox installed.  Or mozilla... or any Gecko browser :x

Suits me! :D

---

### Post by justinflavin on 2005-04-17
since i use KDE as my primary desktop environment, its only natural that i use Konqueror as my default web browser, although i also use Firefox for sites that the KHTML engine has problems with.

the swiss army knife approach of konqueror is something that i like, in that i dont really need to leave konqie in order to get stuff done e.g fish:// makes ssh connections to my servers. 

this newsforge article talks about these less well known konqie features:
[http://software.newsforge.com/article.pl?sid=05/01/20/1822225&tid=130](http://software.newsforge.com/article.pl?sid=05/01/20/1822225&tid=130)

---

### Post by M4v3R on 2006-05-19
Actually, GMail works quite good in Konqueror (full interface), when You turn "Firefox 1.0" fake user-agent string on.

---

### Post by linuxfanatic1024 on 2006-05-27
[QUOTE=nautilus]It's somewhat odd to see this discussion... I've used Konqueror as my only web-browser for, hmm, a year or so?

I've never had a problem with compatibility, and as for rendering issues I doubt it's fair to tackle the browser as the culprit straight off, especially the sites mentioned; frankly the HTML looks atrocious.

But, that said, Konqueror has many features which make it stand far above Firefox, at least on my Ubuntu desktop, such as extremely fast loading, spell checking (which I conveniently ignore frequently), TTS, session resuming, and tabs which don't scroll off your tab-bar after 6 or something silly like that.

Oh hello, I don't even have firefox installed.  Or mozilla... or any Gecko browser :x

Suits me! :D[/QUOTE]
Your user name is Nautilus and you use Konqueror???

Me, I used Firefox for a year and then decided to trash it because it is waaaaaaaaaaay too slow and it's a serious memory hog. I use Konqueror full-time now and am trying to get the Gecko engine to work on it.

---

### Post by tuxcantfly on 2006-05-27
About site incompatibility issues...

Just change the browser identification to either safari or firefox. I think you need konq-plugins for it. Gmail works fine once you change the browser id for mail.google.com to firefox.

---

