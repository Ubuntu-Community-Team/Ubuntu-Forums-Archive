---
title: "posting without javascript enabled : formatting"
date: 2008-05-07
forum: Forum Feedback &amp; Help
---

### Post by bingoUV on 2008-05-07
In the new format of this forum, when we post without javascript enabled special characters are mangled in the post that appears. We cannot catch this glitch in preview. Single quotes appear correctly like ' but , double quotes appear like &quot;. We need to put &ltbr /&gt  inside code tags so that different lines appear different. 

Any tips to format correctly?  

No, I am not enabling javascript. I might have trusted ubuntuforums.org enough to run its javascript, but of course  yahooapis.com will never get my nod. With javascript enabled for ubuntuforums.org but disabled for yahooapis.com, it is impossible to post.

---

### Post by LaRoza on 2008-05-07
> **bingoUV said:**
> In the new format of this forum, when we post without javascript enabled special characters are mangled in the post that appears. We cannot catch this glitch in preview. Single quotes appear correctly like ' but , double quotes appear like &quot;. We need to put &ltbr /&gt  inside code tags so that different lines appear different. 

Any tips to format correctly?  

No, I am not enabling javascript. I might have trusted ubuntuforums.org enough to run its javascript, but of course  yahooapis.com will never get my nod. With javascript enabled for ubuntuforums.org but disabled for yahooapis.com, it is impossible to post.

What do you have against Yahooapis? It is true they are hosted on another server to reduce server loads on the two rather strained servers being used by UbuntuForums.org, but they are the exact same scripts that would be used if they were served from here.

It just serves the scripts not a big deal. If you do not accept the use of the yahooapis, then you have to deal with the effects on the forum.

I am unsure of what you are describing as a bug. I will try it to see if I can post "<> " and such.

---

### Post by bingoUV on 2008-05-07
yahooapis.com belongs to yahoo. What more reason do I need to distrust? I am not even its customer, it will screw me over without second thought. It might post any advertisement script for a nano-cent without verifying if it expoits a recently uncovered javascript vulnerability in firefox. Generally I am a bit lenient with .orgs, but maybe I am wrong to trust ubuntuforums.org too. 

On a more fundamental level, disabling javascript should not cause severe formatting problems. Okay I do not get all the AJAXy goodness, all the pop-over menus etc. But I wonder at the inability of ubuntuforums to provide a correctly working forum for browsers without javascript.

---

### Post by LaRoza on 2008-05-07
> **bingoUV said:**
> yahooapis.com belongs to yahoo. What more reason do I need to distrust? I am not even its customer, it will screw me over without second thought. It might post any advertisement script for a nano-cent without verifying if it expoits a recently uncovered javascript vulnerability in firefox. Generally I am a bit lenient with .orgs, but maybe I am wrong to trust ubuntuforums.org too. 

On a more fundamental level, disabling javascript should not cause severe formatting problems. Okay I do not get all the AJAXy goodness, all the pop-over menus etc. But I wonder at the inability of ubuntuforums to provide a correctly working forum for browsers without javascript.

vBulletin belongs to **Jelsoft Enterprises Limited** I think. Canonical is a customer of this company, therefore a customer of yahooapis as vBulletin makes use of the scripts because of their quality. Yahoo, Jelsoft, and Canonical have never to my knowledge "screwed over" anyone or attempted to. These forum will not have make use of advertisements and the software is uses does not. If you don't trust your browser, which seems to be the case, use another. I recommend Opera. If you don't trust yahoo, firefox, and ubuntuforums.org, then I think you have to sort out some internal issues first. Don't be lenient with .orgs, anyone can get one. In fact, I think only a few domains are restricted like .gov and such. .org, .net, .com, and even .edu can be obtained by anyone.

I have used Lynx to post to this forum, and I don't believe it uses any scripting on the client.

---

### Post by matthew on 2008-05-07
> **bingoUV said:**
> Any tips to format correctly? 
Without enabling javascript? Nope.

You can use a text-based browser like lynx, links2, or w3m, as already recommended, and it *should* work, but it is not a supported means of using the forum.

Otherwise, you are out of luck.

If you can't/don't/won't trust and allow javascript from ubuntuforums.org and yahooapis.com, then the forum functions will not be available to you. Sorry.

---

### Post by bingoUV on 2008-05-08
&quot;

---

### Post by bingoUV on 2008-05-08
I see that you have double quote " in your post. Maybe lynx works better. Thanks for letting me know this. Also glad to know the business relationship of yahoo and canonical.

But this has obscured the original issue. Web pages should 
not need javascript for their basic functionality. It is great for offering additional functionality.

One more problem is that if I allow yahooapis.com when browsing ubuntuforums.org, their javascript might run in other tabs also, which could be displaying other web sites. yahooapis could be serving advertisement scripts to other web sites. Of course the advertisers are not to be trusted, even if yahoo itself is. Google has taken users to malware sites through advertisements(through indescretion rather than malice), why would yahoo be a saint?

---

### Post by p_quarles on 2008-05-08
> **bingoUV said:**
> One more problem is that if I allow yahooapis.com when browsing ubuntuforums.org, their javascript might run in other tabs also, which could be displaying other web sites. yahooapis could be serving advertisement scripts to other web sites. Of course the advertisers are not to be trusted, even if yahoo itself is. Google has taken users to malware sites through advertisements(through indescretion rather than malice), why would yahoo be a saint?
They don't need to be, since YUI is an open source project. The APIs are released under a BSD license, so you can go and take a look at them if you like. 
[http://www.yahooapis.com/yui/articles/faq/](http://www.yahooapis.com/yui/articles/faq/)

---

### Post by LaRoza on 2008-05-08
> **bingoUV said:**
> 
But this has obscured the original issue. Web pages should 
not need javascript for their basic functionality. It is great for offering additional functionality.

One more problem is that if I allow yahooapis.com when browsing ubuntuforums.org, their javascript might run in other tabs also, which could be displaying other web sites. yahooapis could be serving advertisement scripts to other web sites. Of course the advertisers are not to be trusted, even if yahoo itself is. Google has taken users to malware sites through advertisements(through indescretion rather than malice), why would yahoo be a saint?

You are right. However, I would hardly describe UbuntuForums.org as a "web page", as it is a high interactive forum. I test my site (the Learn to Program link in my sig) and make sure it works at 800x600 (and less), without javascript or CSS, and in text mode or in a screen reader. My small site has limited function and is mostly just content (very little of that also). This site and software package is massive. It has to do a lot, and because of this it has higher requirements. The minimum resolution it is supposed to function is in 1024x768 (I think). It works very well in a text browser, which surprised me.

Yahooapis doesn't do that. You can examine the source if you wish :-)

---

### Post by bingoUV on 2008-05-08
> **p_quarles said:**
> They don't need to be, since YUI is an open source project. The APIs are released under a BSD license, so you can go and take a look at them if you like. 
[http://www.yahooapis.com/yui/articles/faq/](http://www.yahooapis.com/yui/articles/faq/)

Thanks for the informative link, but I never doubted yahoo's APIs. I'll be more concerned about whether the server yahooapis.com serves advertisement scripts along with yahoo's APIs, not just when used in ubuntuforums.org, but anywhere else. 
From the general response, I gather that this server does not generally host advertisement scripts, so maybe it is all right. Just that it is a bit hard to come to terms with the descent of ubuntuforums into requiring javascript for basic functionality.

---

### Post by p_quarles on 2008-05-08
> **bingoUV said:**
> Thanks for the informative link, but I never doubted yahoo's APIs. I'll be more concerned about whether the server yahooapis.com serves advertisement scripts along with yahoo's APIs, not just when used in ubuntuforums.org, but anywhere else. 
From the general response, I gather that this server does not generally host advertisement scripts, so maybe it is all right. Just that it is a bit hard to come to terms with the descent of ubuntuforums into requiring javascript for basic functionality.
Nothing is served from yahooapis.com unless ubuntuforums.org specifically asks for it, so no advertising, rest assured.

---

### Post by bingoUV on 2008-05-08
> **LaRoza said:**
> You are right. However, I would hardly describe UbuntuForums.org as a &quot;web page&quot;, as it is a high interactive forum. I test my site (the Learn to Program link in my sig) and make sure it works at 800x600 (and less), without javascript or CSS, and in text mode or in a screen reader. My small site has limited function and is mostly just content (very little of that also). This site and software package is massive. It has to do a lot, and because of this it has higher requirements. The minimum resolution it is supposed to function is in 1024x768 (I think). It works very well in a text browser, which surprised me.



Compared to your relatively static page, ubuntuforums.org is more interactive. Conceivable. But when compared to earlier ubuntuforums.org ? Just 3 weeks ago we were fine. What have we gained? Ability to thank, and count the thanks? wow. 

Inspired by your posting from lynx, I did some testing on various browsers and found interesting results. To summarize, we are incompatible with gecko. 
1. elinks : Supports double quotes perfectly. Presumably without javascript. I used fedora's default build, elinks --version lists a lot of capabilities but not javascript. 
2. Firefox 3 beta 5 : Double quotes do not work without javascript. Ironically, the default browser in hardy. 
3. Firefox 2.0.0.14 : Double quotes do not work without javascript. Ironically, the default browser in feisty and gutsy. 
4. Opera : In windows. Double quotes perfect with js disabled globally.  
5. Konqueror : Linux. Double quotes perfect with js disabled globally.  
6. K-meleon : Windows. Double quotes do not work without javascript. It uses gecko. 

 > **LaRoza said:**
>  Yahooapis doesn't do that. You can examine the source if you wish :-) Yes, I am fairly convinced about yahoo's APIs i.e. the YUI project. Not yet about the server yahooapis.com not serving ad scripts to other web pages. These scripts will get enabled if I allow scripts on ubuntuforums.org, maybe a limitation of the noscript extension of firefox.

---

### Post by LaRoza on 2008-05-08
> **bingoUV said:**
> Compared to your relatively static page, ubuntuforums.org is more interactive. Conceivable. But when compared to earlier ubuntuforums.org ? Just 3 weeks ago we were fine. What have we gained? Ability to thank, and count the thanks? wow. 

Inspired by your posting from lynx, I did some testing on various browsers and found interesting results. To summarize, we are incompatible with gecko. 


The requirements of the previous version were similiar (screen resolution, scripting, etc). The only difference in design is the fact that the scripts are hosted by another site. This was done to save bandwidth, which was scarce to begin with. If one so chose, the scripts could be hosted locally. That may be done in the future, but I don't see a reason why it would be changed at this time.

---

### Post by bingoUV on 2008-05-08
> **LaRoza said:**
> The requirements of the previous version were similiar (screen resolution, scripting, etc). The only difference in design is the fact that the scripts are hosted by another site.

I don't understand. You are saying this just after I have proved that there are so many differences? Without js in gecko we can no longer format code blocks correctly. We can no longer post double quotes without them getting mangled. These features worked without js earlier. At home I used to browse without js enabled and I did not face these issues. These are the differences. How can there be only one difference and that the host of the scripts? Maybe vBulletin have not been kind enough to point out these new limitations.  

Have you forgotten the whole thread? Let us not start over again.

---

### Post by p_quarles on 2008-05-08
> **bingoUV said:**
> I don't understand. You are saying this just after I have proved that there are so many differences? Without js in gecko we can no longer format code blocks correctly. We can no longer post double quotes without them getting mangled. These features worked without js earlier. At home I used to browse without js enabled and I did not face these issues. These are the differences. How can there be only one difference and that the host of the scripts? Maybe vBulletin have not been kind enough to point out these new limitations.  

Have you forgotten the whole thread? Let us not start over again.

Testing *formatting* with **javascript** [size=4]disabled[/size] in [Firefox](mozilla.org).

EDIT: I guess I'm not seeing the problem here. . .

---

### Post by LaRoza on 2008-05-08
> **bingoUV said:**
> I don't understand. You are saying this just after I have proved that there are so many differences? Without js in gecko we can no longer format code blocks correctly. We can no longer post double quotes without them getting mangled. These features worked without js earlier. At home I used to browse without js enabled and I did not face these issues. These are the differences. How can there be only one difference and that the host of the scripts? Maybe vBulletin have not been kind enough to point out these new limitations.  

Have you forgotten the whole thread? Let us not start over again.

I meant to say in the design of the site. The only difference is that the scripts are hosted by another server. They are, of course, not the same scripts that were in the last version of vBulletin.

---

### Post by bingoUV on 2008-05-09
> **p_quarles said:**
> Testing *formatting* with **javascript** [SIZE=4]disabled[/SIZE] in [Firefox]("http://mozilla.org").

EDIT: I guess I'm not seeing the problem here. . .

Did you try  
1. double quotes?  
2. multiple lines in code blocks?

---

### Post by p_quarles on 2008-05-09
> **bingoUV said:**
> Did you try  
1. double quotes?  
2. multiple lines in code blocks?
I will now. 

&quot;Double quotes.&quot;

```
multiple lines of code
inside of a tag block
```Btw, this is Firefox 2.0.0.14, if that makes a difference.  Same thing, this time using the buttons: "Double quotes"  ```
first line second line
```

---

### Post by bingoUV on 2008-05-09
> **p_quarles said:**
> I will now. 

&quot;Double quotes.&quot;

```
multiple lines of code
inside of a tag block
```Btw, this is Firefox 2.0.0.14, if that makes a difference.

&quot;Good for you&quot;.  ```
 1st line : I have already made my  2nd line : test results public 
``` Can you try editing your post and saving it without changes. That is what seems to screw up my double quotes. First posting is all right.

---

### Post by p_quarles on 2008-05-09
> **bingoUV said:**
> &quot;Good for you&quot;.  ```
 1st line : I have already made my  2nd line : test results public 
``` Can you try editing your post and saving it without changes. That is what seems to screw up my double quotes. First posting is all right.
Done. I'm not seeing any difference in my post. 

For what it's worth, I am also disabling uf.org's own javascript in these tests. Are you doing that?

EDIT: the other possible difference here is that I am using the simple text editor. Let me turn on the WYSIWYG and see if I get any different results.

EDIT, part deux: Yeah, the WYSIWYG editor messed it up. So, there is at least one solution for you: use the basic editor. Not ideal for everyone, I realize, but that's an honest workaround.

---

### Post by bingoUV on 2008-05-09
Yes, I disable js from ubuntuforums.org as well. When I enable for ubuntuforums.org and disable for yahooapis, I cannot post at all. Whatever I type vanishes on submit, and it gives an error to the effect of 'type something, moron, what are you posting?' 
That would be great for me except I don't know how to use the basic editor. Anyway these wysiwig buttons are disabled for me.

---

### Post by p_quarles on 2008-05-09
> **bingoUV said:**
> That would be great for me except I don't know how to use the basic editor. Anyway these wysiwig buttons are disabled for me.
It's not hard, and many of us prefer it. Here's a full list of tags:
[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

---

### Post by bingoUV on 2008-05-09
> **p_quarles said:**
> It's not hard, and many of us prefer it. Here's a full list of tags:
[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

Okay, I found the setting at the very bottom of the "Edit Options". It was set to wysiwig, but I used to apply the tags manually anyway as I disabled js. 
```

1st line : hope this 
2nd line : post is 
3rd line : not mangled

```

EDIT : Cool, it seemed to have worked. Thanks. It did not occur to me that editing an option would do it for me.

---

### Post by LaRoza on 2008-05-09
I realized I just missed something here. I always use the plain text editor, and don't know what the others look like. I had an entirely different picture of the problem.

---

### Post by perixx on 2008-05-21
Hello...

I can well understand the troubles of BingoUV. 
I really don't like the use of javascripts, as it's a potential security hole in the first place - it's active content. Not to speak of the privacy issues coming from these kind of techniques; javascripts can just do about anything anything within the browser - reading other cookies, flash-object-information and DOM-objects or maybe even install new 'beneficial' addons in the worst case - correct me, if I'm wrong. 
Besides, it makes the responsiveness of sites slower to a good deal. There's nothing in the forum menus that couldn't be realized in plain html, and a lot faster, that is.

If I want to make sure I don't have companies like yahoo or google reading all of my surfing behaviour right from my browser (or even worse: login information / personalized data), I'd have to surf to those sites in a separate session each, with javascript temporarily enabled (with a tool like 'NoScript'). But I'd have to do that each time over again and close the session after visiting site containing untrustable scripts, in order to have them cleared out (like it's with Ubuntuforums as of late). 

> It just serves the scripts not a big deal. If you do not accept the use of the yahooapis, then you have to deal with the effects on the forum.
> If you can't/don't/won't trust and allow javascript from ubuntuforums.org and yahooapis.com, then the forum functions will not be available to you. Sorry.

Remarks like these show that those issues are obviously not being taken serious at all, nor the complaints against them of us users. Really sad.
Eventually, it would be the site admins' job, to report those worries back to the site owners and urge them to rethink their policy.

P.S. resistance is never futile ;)

perixx

---

### Post by LaRoza on 2008-05-21
> **perixx said:**
> 
I really don't like the use of javascripts, as it's a potential security hole in the first place - it's active content. Not to speak of the privacy issues coming from these kind of techniques; javascripts can just do about anything anything within the browser - reading other cookies, flash-object-information and DOM-objects or maybe even install new 'beneficial' addons in the worst case - correct me, if I'm wrong. 
Besides, it makes the responsiveness of sites slower to a good deal. There's nothing in the forum menus that couldn't be realized in plain html, and a lot faster, that is.

Remarks like these show that those issues are obviously not being taken serious at all, nor the complaints against them of us users. Really sad.
Eventually, it would be the site admins' job, to report those worries back to the site owners and urge them to rethink their policy.

P.S. resistance is never futile ;)

Using any network connection is a "security hole". I think you over estimate the capabilities of ECMAScript and its limitations. It is hard enough to get the same script to work in most browsers, let alone try to exploit security holes. You can't read other cookies and even if you could, login information isn't in the cookies in any site worth going to.

If you really want to see the code for this, it is simple. If you are unable to understand it then take my word that it is not in anyway malicious.

I write ECMAScript scripts for websites, by the way. The only browser with a real issue is Internet Explorer, and those issues have been minimized with the latest updates. Safari had an issue at one point also. These are browser defects, not features of ECMAScript. Fx on Linux doesn't have any real holes as far as I know (at least, none worth exploiting) and Opera is the best browser no matter where you are. (I use Opera)

P.S. Resistance is futile.

---

### Post by bingoUV on 2008-05-21
You are trying to confuse the matter repeatedly. I will say again lest silence be deemed agreement

Yahoo's APIs are not a problem. Being open source, if I am rich, I can hire code monkeys to find a security issue per dollar and generally get the larger bugs discovered. Many javascript developers   might already have scrutinized the code. New check-ins still have to be observed but no one at Yahoo conceivably has the time and inclination to purposefully add malicious code.

Issue is with the server yahooapis.com where it is hosted. There is no guarantee that it hosts only Yahoo's APIs i.e. the YUI project. Not just for ubuntuforums.org, but other sites simultaneously opened. Possibly a limitation of NoScript extension of firefox.


**Javascript vulnerabilities** : It is shameful for an ECMAScript developer to pooh-pooh its vulnerabilities.
1. First let us talk about firefox as it is default in all supported Ubuntu versions. Read [http://www.mozilla.org/projects/security/known-vulnerabilities.html](http://www.mozilla.org/projects/security/known-vulnerabilities.html). Now read workarounds for all critical security issues. In overwhelming majority of cases, it is *Disable JavaScript until a version containing these fixes can be installed. *. 

2. Opera : 
a. A whopping 1.4% market share by best reports, .69% by others. 20-25 times less than firefox's.
b. No public bugzilla. Who knows what vulnerabilities exist?
c. Those wise enough to switch browsers because of security issues are anyway savvy enough to deal with such issues.
d. Extensions ecosystem not that open/vibrant. Cannot do much if some required functionality is missing.

---

### Post by LaRoza on 2008-05-21
> **bingoUV said:**
> You are trying to confuse the matter repeatedly. I will say again lest silence be deemed agreement

Yahoo's APIs are not a problem. Being open source, if I am rich, I can hire code monkeys to find a security issue per dollar and generally get the larger bugs discovered. Many javascript developers   might already have scrutinized the code. New check-ins still have to be observed but no one at Yahoo conceivably has the time and inclination to purposefully add malicious code.

Issue is with the server yahooapis.com where it is hosted. There is no guarantee that it hosts only Yahoo's APIs i.e. the YUI project. Not just for ubuntuforums.org, but other sites simultaneously opened. Possibly a limitation of NoScript extension of firefox.


The code for vBulletin is served from the UbuntuForums.org servers. Here is the code that is static and served straight from our trusted servers:

[html]
<script type="text/javascript" src="http://yui.yahooapis.com/2.5.1/build/yahoo-dom-event/yahoo-dom-event.js?v=370"></script>
<script type="text/javascript" src="http://yui.yahooapis.com/2.5.1/build/connection/connection-min.js?v=370"></script>
<script type="text/javascript">

</script>
<script type="text/javascript" src="clientscript/vbulletin_global.js?v=370"></script>
<script type="text/javascript" src="clientscript/vbulletin_menu.js?v=370"></script>
[/html]

No matter what the yahooapi's server has on it, only "http://yui.yahooapis.com/2.5.1/build/yahoo-dom-event/yahoo-dom-event.js?v=370" and "http://yui.yahooapis.com/2.5.1/build/connection/connection-min.js?v=370"" can be obtained. 

The only way something else could be served is by a direct request. Do you think those two links will be replaced with malicious code? Technically, it is possible. If you think it will be changed with malicious intent, I recommend not using a browser and wget'ing all your content from now on and reading it with a hex editor.

Also, these scripts are likely cached by your browser. If one is so security concerned of this issue, they are dealing with something so improbable that the fact they are using a browser that is not on a live cd and text based shows they are making this a bigger issue than they truly believe.

---

### Post by LaRoza on 2008-05-21
> **bingoUV said:**
> 
**Javascript vulnerabilities** : It is shameful for an ECMAScript developer to pooh-pooh its vulnerabilities.
1. First let us talk about firefox as it is default in all supported Ubuntu versions. Read [http://www.mozilla.org/projects/security/known-vulnerabilities.html](http://www.mozilla.org/projects/security/known-vulnerabilities.html). Now read workarounds for all critical security issues. In overwhelming majority of cases, it is *Disable JavaScript until a version containing these fixes can be installed. *. 

2. Opera : 
a. A whopping 1.4% market share by best reports, .69% by others. 20-25 times less than firefox's.
b. No public bugzilla. Who knows what vulnerabilities exist?
c. Those wise enough to switch browsers because of security issues are anyway savvy enough to deal with such issues.
d. Extensions ecosystem not that open/vibrant. Cannot do much if some required functionality is missing.
Shameful? What do you mean? I don't deny that one can do some "fun" things with an insecure browser. I also am taking into consideration that most people here have no problem visiting wikipedia, my homepage, and youtube without fear.

I also think you underestimate Opera ;) Most people use who rely on extensions on Fx are using them to do something that Opera has built in. Ad and Script blocking seem to be popular. Opera supports this to my satisfaction. Using IRC from Firefox is also possible with an extension. Opera has that built in. Mail? Opera has it. 

I do admit, I use Firefox for two of its extensions. Firebug and Web Developer Toolbar. However, I don't use them when browsing. Actually, because I use them, I don't use that Firefox for browsing (Firebug will run the debugger when an error occurs, simple browsing is very, very tedious with Firebug running.)

---

### Post by bingoUV on 2008-05-21
> **bingoUV said:**
> 
There is no guarantee that it hosts only Yahoo's APIs i.e. the YUI project. **Not just for ubuntuforums.org, but other sites simultaneously opened**. Possibly a limitation of NoScript extension of firefox.
Repeating for the third time.

> **LaRoza said:**
> Shameful? What do you mean? I don't deny that one can do some "fun" things with an insecure browser. 

Did you even read the known vulnerabilities page of the default browser of the OS this forum intends to support? Fun things indeed.

> **LaRoza said:**
> I also am taking into consideration that most people here have no problem visiting wikipedia, my homepage, and youtube without fear.
Most people have no problem clicking on the bouncing bunny with activeX enabled on IE5.0 on unpatched Windows ME. Running as administrator. With data worth more than years of hardwork stored on the same machine. Without backups. So?


> **LaRoza said:**
> 
I also think you underestimate Opera ;) Most people use who rely on extensions on Fx are using them to do something that Opera has built in. Ad and Script blocking seem to be popular. Opera supports this to my satisfaction. Using IRC from Firefox is also possible with an extension. Opera has that built in. Mail? Opera has it. 

Opera's Adblock is so inconvenient that one feels viewing the ad is less of a torture than blocking it. I agree it has more features than FF without extensions. Never tried script block with it. Anyway, let us stick to the "default browser of the OS this forum intends to support". DBOTOTFITS if you please.

> **LaRoza said:**
> simple browsing is very, very tedious with Firebug running.)
I agree wholeheartedly.

---

### Post by LaRoza on 2008-05-21
> **bingoUV said:**
> Repeating for the third time.

Did you even read the known vulnerabilities page of the default browser of the OS this forum intends to support? Fun things indeed.

Opera's Adblock is so inconvenient that one feels viewing the ad is less of a torture than blocking it. I agree it has more features than FF without extensions. Never tried script block with it. Anyway, let us stick to the "default browser of the OS this forum intends to support". DBOTOTFITS if you please.


If it is a concern for you, feel free to block it. The other 500,000 member of this forum will let you know if you are right ;) (I know, not all are active, but still, 17000 or whatever is a lot of people)

No, I didn't. I don't use Firefox for browsing, and I don't write malicious scripts. I have no need to stay up to date on its flaws. 

Right click, click what you don't want, and it is gone. Convenient enough for me. I know, it doesn't have the fine tuning of adblock, but it is enough for me.

Ok, Firefox is the most used browser on this forum. To date, I know of no Firefox security exploits being used by this forums software. 

(Also, Firebug is a very good tool for writing scripts.)

---

