---
title: "Forbidden .. You don't have permission to access /newreply.php on this server."
date: 2018-06-15
forum: Forum Feedback &amp; Help
---

### Post by dragonfly41 on 2018-06-15
When attempting to reply to forum threads I am now seeing this message .. which I suspect only started after I reported an outbreak of spam today .. I have tried Chromium browser, Pale Moon browser, and cleared browser cookies ..

[h=1]Forbidden[/h]You don't have permission to access /newreply.phpon this server.
[HR][/HR]Apache/2.4.7 (Ubuntu) Server at ubuntuforums.org Port 443

---

### Post by Holger_Gehrke on 2018-06-15
Just posting to see whether it's a general server problem or just you ... Your post is 31 Minutes old and still the newest post in "Ubuntu Official Flavours Support" ...

Holger

Edit: Obviously my reply got through, so either it was a general problem that got cleaned up or it's just you.

---

### Post by dragonfly41 on 2018-06-16
I was trying to add a reply to this thread which I had previously responded to.
 
 [https://ubuntuforums.org/showthread.php?t=2394220](https://ubuntuforums.org/showthread.php?t=2394220)
 
 However again today I can't add a reply.
 
Curious, I have researched this and it seems that any OP can ignore posts from specified users.
 
 [https://ubuntuforums.org/profile.php?do=ignorelist](https://ubuntuforums.org/profile.php?do=ignorelist)
 
 I learned this from reading here ...
 
 [https://steamcommunity.com/discussions/forum/1/620712364021294711/](https://steamcommunity.com/discussions/forum/1/620712364021294711/)
 
 > Most forum software features blocking (aka ignore) tools. Take vbulletin for example. One of the most popular forum platforms on the internet - if not *the* #1 forum platform. Users can add other users to their ignore list, and they will never have to look at their posts again.
 
Ubuntu also uses vbulletin.  If that is the case here it is the first time I have encountered being blocked from posting to a thread.

---

### Post by thenailedone on 2018-06-16
I believe that all the ignore function would do is to not show a specific users post to the person that has set it. They can't make another users posts invisible to others.

---

### Post by PaulW2U on 2018-06-16
> **thenailedone said:**
> I believe that all the ignore function would do is to not show a specific users post to the person that has set it. 
And even then a link is provided for the hidden post to be revealed as you do get an indication that the user you have ignored has posted.
> **dragonfly41 said:**
> I was trying to add a reply to this thread which I had previously responded to.
 
 [https://ubuntuforums.org/showthread.php?t=2394220](https://ubuntuforums.org/showthread.php?t=2394220)
Does your reply include any unusual character combinations? I occasionally get permission errors when searching the forums with large amounts of text that include, in my opinion, too many punctuation characters. If I edit my query by removing some of them then the search proceeds. Is there anything unusual about the formatting of your intended post?

---

### Post by dragonfly41 on 2018-06-16
Your thesis seems to be correct.  I have just tried pasting intended post here and I received the same Forbidden message.

I will try cutting out some links etc.

---

### Post by dragonfly41 on 2018-06-16
I have succeeded in posting (without seeing the Forbidden message) by removing a simple code block I had inserted with html code inside.

---

### Post by PaulW2U on 2018-06-16
> **dragonfly41 said:**
> I have succeeded in posting (without seeing the Forbidden message) by removing a simple code block I had inserted with html code inside.
So I see.

Whether the content of your post was rejected by vBulletin's programming, Canonical's installation of the software or the settings that the forum administrators can change, I guess as mere mortals here, we'll never know the real reason for you not being able to post what you originally intended.  :)

---

### Post by coffeecat on 2018-06-16
> **dragonfly41 said:**
> I have succeeded in posting (without seeing the Forbidden message) by removing a simple code block I had inserted with html code inside.

Aha!

Speaking as a mere forum admin who is bewildered by the details of whatever Canonical IS has got up to in tightening security after a breach a few years ago, I can say one thing. Certain strings, whether in searches or in posts or in pm's, will trigger the firewall and will give you the forbidden message. If you get the "don't have permission to access..." message, try fine-tuning whatever it is you are trying to post/pm/search for. Some html code definitely sets off alarm bells. 

The other thing is if you have script output that is too long - sorry, I've forgotten the limit - that may also cause problems, which is why we suggest using pastebin if you have wireless script output or similar to include in your post. 

As an aside, the ignore function is nothing to do with this. No one (except forum staff) can block you from posting. If you were to be blocked from posting by forum staff, you'd be told why! :wink: But rest assured, there's nothing in your profile settings that would stop you from posting.

---

### Post by SeijiSensei on 2018-06-17
Let's try a dangerous string.

**DO NOT RUN THIS COMMAND. IT WILL DELETE ALL YOUR FILES.**

sudo rm -rf /

or 

```
sudo rm -rf /
```

If I were scanning forum posts for dangerous content, this one would be high on my list.

dragonfly, did you put your code in [noparse]```

```[/noparse] tags, and it was still rejected?

---

### Post by coffeecat on 2018-06-17
> **SeijiSensei said:**
> Let's try a dangerous string.

**DO NOT RUN THIS COMMAND. IT WILL DELETE ALL YOUR FILES.**

sudo rm -rf /

or 

```
sudo rm -rf /
```

If I were scanning forum posts for dangerous content, this one would be high on my list.

dragonfly, did you put your code in [noparse]```

```[/noparse] tags, and it was still rejected?

That completely and utterly misses the point of what the firewall rules are there for. Let's keep this real, please.

---

### Post by SeijiSensei on 2018-06-17
Why?  If that code isn't "dangerous," what kind of dangerous content is being filtered?  dragonfly suggests it was a block of HTML code.  That is almost certainly less dangerous than my posting.

> I have succeeded in posting (without seeing the Forbidden message) by removing a simple code block I had inserted with html code inside. 

Did it contain dangerous Javascript code?  How exactly might a block of HTML code itself be a threat?

---

### Post by DuckHook on 2018-06-17
@SeijiSensei

You and coffeecat may be commenting at cross purposes…

coffeecat was referring to code that may be dangerous to the functioning of the forums. You are referring to code that is dangerous to users.

I believe that Canonical IT firewalled a whole set of string types that they deemed dangerous to forum functionality a while back. As forum staff, we do not know what those firewall rules are (the staff administer the forum content; Canonical IT administer forum functionality).

---

### Post by dragonfly41 on 2018-06-17
Sorry for creating a storm. I didn't realise this discussion was ongoing.

I created a file of the problematic codebox content to upload it for further information but when I try to upload it as attachment I see this message .. I guess the firewall is doing its business ..

[B]ubuntuforums.org says
the following errors occurred:

test.html  Invalid File[/B]

Instead of uploading I have placed it in pastebin ...

[https://pastebin.com/gxbtYfMa](https://pastebin.com/gxbtYfMa)

I really don't know why this code is regarded as dangerous.

But on another point if such scripts are thrown out for whatever reason I suggest that the firewall should give a more meaningful error message to educate the poster.

[COLOR=#b22222]**[Later edit]**[/COLOR]

To answer question from @SeijiSensei the html code was placed inside code tags

---

### Post by PaulW2U on 2018-06-17
I've just gone to the top of this forum page and inserted the following text into the search box:
> But on another point if such scripts are thrown out for whatever reason I suggest that the firewall should give a more meaningful error message to educate the poster. 
The quote is of course taken from dragonfly41's previous post. I received the following error:
```
Forbidden

You don't have permission to access /search.php on this server.
```
More meaningful error messages would be most helpful on searches too.

---

### Post by dragonfly41 on 2018-06-18
I have just noticed that html extension (which I failed to upload) is not in the list of valid extensions
in Manage Attachments.

[COLOR=#777777]Valid file extensions: bmp bz2 deb doc gif gp3 gp4 gp5 gpl gz jpe jpeg jpg odg odp ods odt pdf png psd py sh svg tar tg txt xcf zip


[/COLOR]

---

