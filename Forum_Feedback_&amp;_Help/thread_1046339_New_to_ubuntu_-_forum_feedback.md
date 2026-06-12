---
title: "New to ubuntu - forum feedback"
date: 2009-01-21
forum: Forum Feedback &amp; Help
---

### Post by goaliefight on 2009-01-21
This forum experience is overwhelming. The forum layout is very "busy". Maybe it's something about the color scheme but it really throws my senses off. Am I alone? I just wanted to throw my two cents in. Hope you find this feedback helpful.

PS > There are some great features on here. I hope I can get used to whatever it is about the layout and colors that is overwhelming my senses.

---

### Post by kellemes on 2009-01-21
Maybe it's because the forum is busy to begin with.. I mean, I lot of threads, a lot of subforums.
The colorscheme I find more relaxing than busy.
I do think the active-member list should be removed. Or placed in some sort of seperate part of the forums, not in view anyway, having more then 12 thousand usernames on the frontpage seems too much.

---

### Post by Joeb454 on 2009-01-21
> **kellemes said:**
> Maybe it's because the forum is busy to begin with.. I mean, I lot of threads, a lot of subforums.
The colorscheme I find more relaxing than busy.
I do think the active-member list should be removed. Or placed in some sort of seperate part of the forums, not in view anyway, having more then 12 thousand usernames on the frontpage seems too much.

It only shows logged in *members*, not all active users.

That said I think you might be right, it could reduce the load a little as well :)

---

### Post by Elfy on 2009-01-21
You can minimise it so you don't have to see them all - but I liked when we could set up so as not to see specific forums.

---

### Post by Joeb454 on 2009-01-21
> **forestpixie said:**
> You can minimise it so you don't have to see them all

Hmm...I'd imagine that still has to run the query on the database regardless, though I'm not sure.

I remember at one point it was a link to a who's online page, which made a bit more sense.

Either way, I don't think this is specifically what the OP was referring to ;)

I actually prefer this forum layout to some of the other forums I've seen recently, though that *could* be because I do come here often ;)

---

### Post by PriceChild on 2009-01-21
> **Joeb454 said:**
> Hmm...I'd imagine that still has to run the query on the database regardless, though I'm not sure.I've a sneaking suspicion it doesn't... minimize and reload the page. Then expand it and notice it takes a short while. No technical backing to my opinion of course!

---

### Post by p_quarles on 2009-01-21
> **Joeb454 said:**
> Hmm...I'd imagine that still has to run the query on the database regardless, though I'm not sure.

I remember at one point it was a link to a who's online page, which made a bit more sense.

Either way, I don't think this is specifically what the OP was referring to ;)

I actually prefer this forum layout to some of the other forums I've seen recently, though that *could* be because I do come here often ;)
It may or may not run a query, but it definitely doesn't render if you have the list minimized. It allows the front page to load noticeably more quickly.

---

### Post by I-75 on 2009-01-21
> **goaliefight said:**
> This forum experience is overwhelming. The forum layout is very "busy". Maybe it's something about the color scheme but it really throws my senses off. Am I alone? I just wanted to throw my two cents in. Hope you find this feedback helpful.

PS > There are some great features on here. I hope I can get used to whatever it is about the layout and colors that is overwhelming my senses.

 Welcome to the forum.

---

### Post by jenkinbr on 2009-01-21
> **forestpixie said:**
> You can minimise it so you don't have to see them all - but I liked when we could set up so as not to see specific forums.
Whoa - what?  never knew that, trying now.

I learn something new ever day.

I personally never go to the front page unless I have no other choice.  I always go to this link - [http://ubuntuforums.org/forumdisplay.php?f=130](http://ubuntuforums.org/forumdisplay.php?f=130) - labeled The Ubuntu Forums Community.

---

### Post by drubin on 2009-01-22
> **PriceChild said:**
> I've a sneaking suspicion it doesn't... minimize and reload the page. Then expand it and notice it takes a short while. No technical backing to my opinion of course!

It does still run the query and load the html it is just hidden so the speed is only improved in your browsers rendering time.

ie 
[HTML]<tbody id="collapseobj_forumhome_activeusers" style="display:none;">
	<tr>
..... Sniped to save sanity
	</tr>
</tbody>[/HTML]

[HTML]<tbody id="collapseobj_forumhome_activeusers" style="">[/HTML]

Ie only the css style is set to not be shown. It would still run the qurey still output the text to the users browser screen, and still have the same load on the servers/proxy server. It would decrease the load on your web browser though.

I do vote for having the query/template code removed this way even if it does run the query it wont have to generate/transfer all that html.

---

### Post by ubuntu-geek on 2009-01-22
We can look into doing this. It would cut down on some database traffic and drubin is correct, the query still runs regardless if it is minimized or not. However, the query gets cached for 30 minutes per user. The main reason for leaving it enabled is for people to see which staff are online.

---

### Post by drubin on 2009-01-22
> **ubuntu-geek said:**
> We can look into doing this. It would cut down on some database traffic and drubin is correct, the query still runs regardless if it is minimized or not. However, the query gets cached for 30 minutes per user. The main reason for leaving it enabled is for people to see which staff are online.

Server(db)->Server(web) -> Server(cache) = very fast connection.
Server(cache)->users = Slow (relatively) that means that while the page is loading it adds/ques up extra requests to the cache server.

Either way it will speed up page transfer and rendering time.

Isn't the [showgroups]("http://ubuntuforums.org/showgroups.php") page show which members are online? guess not. But would be a much better place.

btw I do think it is South Africa -> UK connection issues I have been having issues with websites hosted in UK the whole day.

---

### Post by hyper_ch on 2009-01-22
> **ubuntu-geek said:**
> The main reason for leaving it enabled is for people to see which staff are online.
Well, that's a good reason. However, I wonder, how much additional pressure does it put on the servers?

---

### Post by ubuntu-geek on 2009-01-22
> **hyper_ch said:**
> Well, that's a good reason. However, I wonder, how much additional pressure does it put on the servers?
Not that much to be honest.. But we'll do some metric's on it.

---

### Post by hyper_ch on 2009-01-22
I guess if it gets cached for 30min then it does not put much pressure on it... oh well, you do a great job :)

---

### Post by Joeb454 on 2009-01-22
If it's to show which staff are online, perhaps have something that only shows online staff (unless that's a more intense query to run of course) with a link to "Show all online" so you can still view everybody that's online if need be.

Just a random thought :)

---

### Post by Rocket2DMn on 2009-01-22
I personally like being able to see who is online, but it's true I'm mostly checking for staff.  If we find that it is worth some adjustments, I am not opposed to disabling it on the front page, hiding it by default, or moving it to a separate query page from something like a "See who is currently online" link.  I would hate to see the feature disappear completely, but I'm all for tweaking the speed!  :)

---

### Post by bapoumba on 2009-01-22
+1.

---

### Post by jenkinbr on 2009-01-22
> **Rocket2DMn said:**
> I personally like being able to see who is online, but it's true I'm mostly checking for staff.  If we find that it is worth some adjustments, I am not opposed to disabling it on the front page, hiding it by default, or moving it to a separate query page from something like a "See who is currently online" link.  I would hate to see the feature disappear completely, but I'm all for tweaking the speed!  :)
I +1 that as well.  Great idea.

Those interested in the online users can check, those who are not interested, can ignore it.  Sounds like a win-win to me.

---

