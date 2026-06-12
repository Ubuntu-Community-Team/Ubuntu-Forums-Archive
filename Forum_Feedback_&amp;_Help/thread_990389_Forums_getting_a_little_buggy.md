---
title: "Forums getting a little buggy?"
date: 2008-11-22
forum: Forum Feedback &amp; Help
---

### Post by jimmy the saint on 2008-11-22
I have been on these forums for a while now and I have noticed more buggy behavior recently.

1- Around 1 in 10 times that I respond to a post, the browser hangs and I get a message that I am only able to post every twenty seconds.  I am then kicked to the reply window, with my reply printed in ready to be submitted.  The funny thing is, it has already been posted.  So if I hit post, I get kicked to another error page indicating that I shouldn't be double posting!

2- There are a lot more hangs where pages will not load for approx 15 seconds.  It is a communication issue, as, while waiting, I will open a few threads to peruse and all will hang then load at the same time.  

These are not really big issues for me, but I wanted to share them in case no one else had.  Still the best forums I've had the privilege of using!  Keep up the good work!

JTS

---

### Post by Elfy on 2008-11-22
All to do with the addition of a new server not pulling it's weight I would suspect - or something a bit more technical meaning much the same thing :)

---

### Post by Rocket2DMn on 2008-11-24
I believe an additional webserver was added a [few weeks ago]("http://ubuntuforums.org/showthread.php?t=974133"), but the database is still being overworked.  Just look on the homepage to see how many users are active at any given time, it's enormous.

---

### Post by Elfy on 2008-11-24
Shame they can't split it so that those of us that are bothered to register and contribute get a benefit :)

But hey I'm not complaining it's so much more usable than it was a while back :)

---

### Post by dariusdwtt on 2008-12-08
I usually have to log in about 5 times till it realises I'm logged in, then once I'm logged in I try post and it tells me I have to log in...???

So when the going's good I don't log out just stay logged on semi-perminently...

...guess what just happened

<quote>
You do not have permission to perform this action. Please refresh the page and login before trying again.
</quote>

logged in again.

and

<quote>
 You do not have permission to perform this action. Please refresh the page and login before trying again.
 </quote>

---

### Post by dariusdwtt on 2008-12-08
Don't know why it's called a quick post...

---

### Post by luca_linux on 2008-12-09
Maybe deleting the accounts of users who haven't logged in for the last 2-3 years would make the DB a bit smaller and speed up the performance a little. :)
The actual overload due to connections wouldn't benefit from this though.

---

### Post by lukjad on 2008-12-09
Well, that isn't exactly very nice...

---

### Post by luca_linux on 2008-12-09
> **lukjad007 said:**
> Well, that isn't exactly very nice...
Yeah, I do know, but just think about how many (not active) accounts there will be within 5-10 years from now. I think it's an action that will be necessary someday anyway. So, they could just make it a rule on a regular basis, for example just as Google does for Gmail accounts, or Microsoft does for Live accounts, etc.

---

### Post by luca_linux on 2008-12-09
IMHO the same applies for threads...I don't see the point of keeping threads which are 10 years old or so.
For example, in 2016 who will actually be reading this thread? :P

---

### Post by Rocket2DMn on 2008-12-09
The idea you put forward has been discussed before, but I don't believe anything came of it.  The size of the database shouldn't be much of a problem, just the number of active connections and queries/writes.  Vbulletin is designed to handle large databases and it does it quite well.  

I don't know much about Vbulletin or our database configuration, but I would imagine that the forums and database are configured in such a way, that depending on what you are trying to view on the forums, access to a single entry in the database's hard drive should be achievable on O(1) - constant time.  Of course, a single page in a thread has many accesses (user info, post info, thread info - usually at only 10 posts per page).  Everything is stored with a number - users have a user number, there are thread numbers, and there are post numbers : this should be how the database is indexed, hence access is O(1).  In this case, the database is simply a collection of simple tables.  So, since we're not changing the number of posts on a page, or the number of threads visible on a forum page, no time would be saved by simply deleting info from the database.

Now assume that the database can't pull a query in O(1) because it's not using some type of large array to index thread, post, and user numbers.  If the database is stored in a tree type structure or it simply searches its tables with a binary search algorithm, then finding your query is O(log(n)).  So if you chopped off half the database, you would save 1 hard disk query.  However, since we are using a linear set of numbers to archive users, threads, posts, etc., this shouldn't be necessary and my first example seems more likely.

Of course, this is all coming from my head, I don't actually know what the database structure looks like - the point is that deleting part of the database won't save you much if anything.

Other types of databases do benefit from being smaller, like relational databases that require searching through the data to find what you are looking for.

---

### Post by jenkinbr on 2008-12-09
> **dariusdwtt said:**
> I usually have to log in about 5 times till it realises I'm logged in, then once I'm logged in I try post and it tells me I have to log in...???

So when the going's good I don't log out just stay logged on semi-perminently...

...guess what just happened

<quote>
You do not have permission to perform this action. Please refresh the page and login before trying again.
</quote>

logged in again.

and

<quote>
 You do not have permission to perform this action. Please refresh the page and login before trying again.
 </quote>
Log out, delete your ubuntuforums.org cookie and restart firefox - this happened to me, and that fixed it.

---

### Post by luca_linux on 2008-12-09
> **Rocket2DMn said:**
> The idea you put forward has been discussed before, but I don't believe anything came of it.  The size of the database shouldn't be much of a problem, just the number of active connections and queries/writes.  Vbulletin is designed to handle large databases and it does it quite well.  

I don't know much about Vbulletin or our database configuration, but I would imagine that the forums and database are configured in such a way, that depending on what you are trying to view on the forums, access to a single entry in the database's hard drive should be achievable on O(1) - constant time.  Of course, a single page in a thread has many accesses (user info, post info, thread info - usually at only 10 posts per page).  Everything is stored with a number - users have a user number, there are thread numbers, and there are post numbers : this should be how the database is indexed, hence access is O(1).  In this case, the database is simply a collection of simple tables.  So, since we're not changing the number of posts on a page, or the number of threads visible on a forum page, no time would be saved by simply deleting info from the database.

Now assume that the database can't pull a query in O(1) because it's not using some type of large array to index thread, post, and user numbers.  If the database is stored in a tree type structure or it simply searches its tables with a binary search algorithm, then finding your query is O(log(n)).  So if you chopped off half the database, you would save 1 hard disk query.  However, since we are using a linear set of numbers to archive users, threads, posts, etc., this shouldn't be necessary and my first example seems more likely.

Of course, this is all coming from my head, I don't actually know what the database structure looks like - the point is that deleting part of the database won't save you much if anything.

Other types of databases do benefit from being smaller, like relational databases that require searching through the data to find what you are looking for.

 Ok, got it. Thank you for the detailed explanation. :)

---

### Post by dariusdwtt on 2008-12-09
nope no luck.

---

### Post by drubin on 2008-12-09
> **Rocket2DMn said:**
> The idea you put forward has been discussed before, but I don't believe anything came of it.  The size of the database shouldn't be much of a problem, just the number of active connections and queries/writes.  Vbulletin is designed to handle large databases and it does it quite well.  

I don't know much about Vbulletin or our database configuration, but I would imagine that the forums and database are configured in such a way, that depending on what you are trying to view on the forums, access to a single entry in the database's hard drive should be achievable on O(1) - constant time.  Of course, a single page in a thread has many accesses (user info, post info, thread info - usually at only 10 posts per page).  Everything is stored with a number - users have a user number, there are thread numbers, and there are post numbers : this should be how the database is indexed, hence access is O(1).  In this case, the database is simply a collection of simple tables.  So, since we're not changing the number of posts on a page, or the number of threads visible on a forum page, no time would be saved by simply deleting info from the database.

Now assume that the database can't pull a query in O(1) because it's not using some type of large array to index thread, post, and user numbers.  If the database is stored in a tree type structure or it simply searches its tables with a binary search algorithm, then finding your query is O(log(n)).  So if you chopped off half the database, you would save 1 hard disk query.  However, since we are using a linear set of numbers to archive users, threads, posts, etc., this shouldn't be necessary and my first example seems more likely.

Of course, this is all coming from my head, I don't actually know what the database structure looks like - the point is that deleting part of the database won't save you much if anything.

Other types of databases do benefit from being smaller, like relational databases that require searching through the data to find what you are looking for.

Nice explanation but indexes are not always as simple as you have made them out to be.

Often the forums are indexed by "thread" so when you are viewing a *large* thread it has to look through all the forums posts even if it is only going to display from 10 -20.

I mean I have only ever seen phpbb3's/a few others code/db this is what seemed to be the standard.

*hint* the bump thread.

---

### Post by lukjad on 2008-12-09
*hint* Leave the BUMP thread ALONE. :evil:

j/k

---

### Post by Rocket2DMn on 2008-12-09
> **drubin said:**
> Nice explanation but indexes are not always as simple as you have made them out to be.

Often the forums are indexed by "thread" so when you are viewing a *large* thread it has to look through all the forums posts even if it is only going to display from 10 -20.

I mean I have only ever seen phpbb3's/a few others code/db this is what seemed to be the standard.

*hint* the bump thread.

Thanks drubin, I know it is more complicated than that, but I didn't want to go into too many details of how DBMS's work with search queries, organization, and hard disk calls, reads, and writes.  I don't think this forum goes through all the posts since posts are actually independent of of the thread (we can easily move a post between threads without changing the post's number, just like we can move a thread between forums without changing its number).  I would hypothesize that the thread stores the numbers of all its posts and a post stores the number of the thread it is in.  If the BUMP thread had to read all 30,000 of its posts, the forum would probably crash on every request!

---

### Post by fiona-conn on 2008-12-09
I've been experiencing some issues myself; now and then, it does take a few minutes for a page to show up. Such has been known to fail now and then with a 502 Proxy error. Refreshing sometimes helps, but not always.

---

### Post by jenkinbr on 2008-12-09
The number of posts that occure in the bump thread, or any thread in the games section for that matter, is probably minimal in comparison to the rest of the forums.

For example, Absolute beginner Talk has a total of 2259 pages at the time of this post, and gets way more attention than the cafe games forum.  Many of the general support catigories also have page counts in or near the 1000 range.

However, I don't think the issue has to do with the amount of posts - That should not be an issue.  The problem probably has more to do with this:

> Currently Active Users: 13361 (948 members and 12413 guests)

That is a lot of active users.  I imagine it would be more, but we probably just lost a bunch when the forums started spitting HTTP 502's and 503's (Proxy error and down for maintainance errors, respectively.

And check this out:
> Most users ever online was 24,635, 4 Weeks Ago at 12:39 PM.

Talk about a lot of server activity.

---

### Post by bapoumba on 2008-12-09
> **jenkinbr said:**
> Talk about a lot of server activity.
Yes, probably. When I wake up early enough and browse the forums during my early morning (UTC +1), I never have any problem. During the Americas daytime, it occurs more frequently.

---

### Post by drubin on 2008-12-09
> **Rocket2DMn said:**
> Thanks drubin, I know it is more complicated than that, but I didn't want to go into too many details of how DBMS's work with search queries, organization, and hard disk calls, reads, and writes.  I don't think this forum goes through all the posts since posts are actually independent of of the thread (we can easily move a post between threads without changing the post's number, just like we can move a thread between forums without changing its number).  I would hypothesize that the thread stores the numbers of all its posts and a post stores the number of the thread it is in.  If the BUMP thread had to read all 30,000 of its posts, the forum would probably crash on every request!

There is *only* one way to check this. print out the query that is generated to get the posts for the thread.

then run 
EXPLAIN query; in a sql and see how many rows are returned/examined and compare that.

now since none of us have access to the data base the next alternative would be to fake it with an installation of vBulletin and throw many many forms/threads/posts into it and then explains the queries.
> 
If the BUMP thread had to read all 30,000 of its posts,

Very simplified version would be
```
SELECT * FROM posts INNER JOIN threads ON (thread_id) WHERE thread_id=123123 LIMIT 200,220
```
get 20 posts from the 200th the posts for thread 123123 

If you have indexes on thread_id. being it would only examin the posts that pertain to this thread.

Another option is that the postcount is also indexed. ie the post number for each thread if these were also indexed you could have something like 
```
SELECT * FROM posts INNER JOIN threads ON (thread_id) WHERE thread_id=123123 AND post_count BETWEEN 200 AND 220
```

this would only examine 20 posts....

This post is starting to turn into a technical discussion so I am going to leave it unless it is moved to ppt.  :)

note: I actually have no idea how the vBulletin db is indexed/coded.

---

### Post by luca_linux on 2008-12-09
> **bapoumba said:**
> Yes, probably. When I wake up early enough and browse the forums during my early morning (UTC +1), I never have any problem. During the Americas daytime, it occurs more frequently.
Yeah, I noticed that too.

---

### Post by Elfy on 2012-07-25
> **luca_linux said:**
> IMHO the same applies for threads...I don't see the point of keeping threads which are 10 years old or so.
For example, in 2016 who will actually be reading this thread? :P

someone did in 2012

these issues are so old I wasn't staff when I posted the last time

I am now

closed

---

