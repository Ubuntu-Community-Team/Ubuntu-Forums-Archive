---
title: "Query about forum queries"
date: 2014-10-17
forum: Forum Feedback &amp; Help
---

### Post by Cbhihe on 2014-10-17
Something bugs me everytime I set out to search UF's posts for a solution to a particular pbm. 
Namely:

-1- when I use keyword (kw) search, selecting "Search entire post" or "Search multiple content types", I more often than not get results that have NOTHING to do with my search. 

A couple of examples are if I look for posts whose body specifically contains the vimrc setting "mouse=a" or, in an altogether different area, the command "crontab -e".
Apparently UF's search engine takes the liberty to include posts solely on the basis of the ocurrence of "mouse" or "crontab" and produces results along that line. Sooo... I am left with sifting through 350 posts to find a couple of irrelevant "mouse=a" ocurrences or of "crontab -e". 

Plainly put I think _anybody_'s time is worth more than that. 

In fact I am not even sure that UF's search engine does not include them because they also conform to the more general patterns "mouse" or "crontab", i.e. a case where the search pattern would be determined solely by the first string. 
Instead my intention was precisely and clearly inverse: i.e. I want to restrict the search to the complete kw strings, with the non alphanumeric in the case of "mouse=a" and with the blank in the case of "crontab -e".
 
Is there way to force UF's search engine to comply strictly with the kws ? 

-2- search by multiple kws or multiple tags are also two things I have never managed to acheive; only the first item (kw or tag) seems to be taken into account with blank separators or comma separators.

Any thought anyone ?
-ced

---

### Post by tgalati4 on 2014-10-17
The search box is actually a suggestion box.  The results returned are suggestions.  I only use keyword search to search my own posts (using Advanced Search, search by username and keyword) to find an old post that might be helpful to a current problem.  That is what I find UF search most helpful for.  For everything else I use PopularPages for topics and google (with and without the site: keyword).

So basically, it you know the solution to the problem, the search box is helpful for finding that solution.  It's sort of like a recursive acronym.  It make no sense unless you know about the acronym and the terms that make it up.  Context does not help to define a recursive acronym.  Similarly, the search box does not help find the solution unless you already know the solution--that way you can put in a very specific keyword to find a helpful post.

I find the search box in PopularPages is more helpful.  For instance *vimrc* returns:

[https://help.ubuntu.com/community/VimHowto](https://help.ubuntu.com/community/VimHowto)

Search *catfood*.  You will find a lot of my posts.  Search works pretty well in this case.

A Haiku:

A metaquery:
Crappy search in the forums?
Finds *catfood* OK.

---

### Post by Cbhihe on 2014-10-17
;-D well done for *catfood* !! 
 However I am more into pizza and pasta myself. Of course I don't mean that to be disparaging in any way ! And I like cats...  ;-DD

More to the point, I really think that there should be a sticky or something in UF for newbies to understand that "search" really means "loose-suggestion-if-you're-lucky!".
Cheers,

---

### Post by ajgreeny on 2014-10-17
I have given up using the forum search and instead use either [Googlubuntu]("http://www.googlubuntu.com/") or my own [Ubu-Search]("https://www.google.co.uk/cse/publicurl?cx=003847201077524938900:ukjniuf1wao") which seem to give me much better results, though without using more advanced search terms, they both will give you a lot of results.

---

### Post by coffeecat on 2014-10-17
The inbuilt vbulletin search utility is, in fact, far more powerful than most people give it credit for. You simply have to learn how to use in properly, particularly the use of boolean operators: AND, OR and NOT.

[http://www.vbulletin.org/forum/showthread.php?t=253432](http://www.vbulletin.org/forum/showthread.php?t=253432)

I use it for most of my searches and rarely have to use google's *site:ubuntuforums.org <search string>*.

---

### Post by tgalati4 on 2014-10-17
So, Ubuntu Forums search is helpful if you know the answer AND use specific keywords OR you have a lot of time to go through many posts but NOT if you don't know what you are doing or even how to formulate the problem.

I stand corrected.

One of the problems of using the search function in a forum that is 10 years old is that there are a lot of posts.  So you will get a lot of hits unless you choose very specific keywords that are directly related to solving your problem.  Knowing these keywords means that you know the solution--and then you don't need to use the search.

---

### Post by Cbhihe on 2014-10-20
Well, well, what do you know ?...
 @tgalati4: It looks like your "*catfood*" keyword has attracted the right kind of attention (post #5)...

Now seriously, guys'n gals, I know that not everybody knows or has to know George Boole and the mathematical tools he bequeathed us. I happen to use them on a daily basis. 
It seems to me that the problem at hand is far more basic than not knowing how to use a vBulleting search engine ... or even kind of making a "very" educated guess at the answer to a question.

The problem is for instance that if you look for "[FONT=courier new]mouse=a[/FONT]" (a very "precise" kw consisting of one string, unless I miscontrue the meaning of the quote sign for the search engine), you will get 96% noise because the search engine spews out results for the keyword "mouse", and accessorily 2-4% for "mouse=a" [filters: within the post, with at least 1 reply, within the last 6 months]. 
That, as I elaborated in my post at the top of this thread, smacks of a search engine that does not interpret an arbitrary string as what it is: an arbitrary string "[FONT=courier new]mouse=a[/FONT]". 

@coffeecat: Is there more to it than the link you provide ? Because if not, then basically that search engine looks waaaay too rudimentary... or its underlying DB's entries are not properly tagged or queried or something else or all of the above... And I hope I am wrong in that.[SIZE=2][/SIZE]

---

### Post by coffeecat on 2014-10-20
> **Cbhihe said:**
> The problem is for instance that if you look for "[FONT=courier new]mouse=a[/FONT]" (a very "precise" kw consisting of one string, unless I miscontrue the meaning of the quote sign for the search engine), you will get 96% noise because the search engine spews out results for the keyword "mouse", and accessorily 2-4% for "mouse=a" [filters: within the post, with at least 1 reply, within the last 6 months]. 

First, when I posted before I had limited time and posted in haste. I should have mentioned that, yes indeed, the vbulletin search has flaws, but that it can perform better than some people think. Apologies for not being precise. That all being said, you have identified one very strange flaw. You are right - "mouse=a" (with quotes) produces a lot of noise. It simply shouldn't. If we search for "mouse=a" then we want results only that contain that particular string - period. 

However, I have noticed something odd. It wouldn't be correct to say that it is spewing out results for the keyword "mouse". If you compare the results for "mouse=a" and "mouse" they are different. If you now look carefully at the results for "mouse=a", every result which contains "mouse" but not "mouse=a" has the word "a" or "and" after "mouse". As well as looking for "mouse=a" it has served up "mouse a".

Bizarre.

Whether this is a bug and whether there is a way round this particular irritation, I don't know. Again, I have limited time to post, but I'll try to look into this because there were a few other points that I wanted to make.

---

### Post by Cbhihe on 2014-10-20
Thanks ! ... and the same thing occurs with another already mentionned example keyword containing a space : "[FONT=courier new]crontab -e[/FONT]". It looks like the search engine sparses terms along strict alphanumerical lines. Could spaces and non alphanumerical signs such as "=" or "-" be construed as separators ?  
-ced.

---

### Post by tgalati4 on 2014-10-20
vBulletin is proprietary code, so who knows how the search function works.  My guess is that special characters mess up the search algorithm.  Don't use them.

I use the term *catfood* as a meme to denote something which has an [unknown quality]("http://ubuntuforums.org/showthread.php?t=1585183&highlight=catfood") to it.  It is related to the March 2007 pet food scare that caused the death of several thousand pets because of unknown ingredients (which later turned out to be toxic) in certain pet food products.  If I have offended any pets, especially cats, I apologize.

I do like tunafish though.

So, a crappy search engine in a large forum returns generally crappy results, but, using boolean expressions can improve results:  *catfood* AND *quality* returns only two results.  This thread and one about [lithium batteries]("http://ubuntuforums.org/showthread.php?t=1429828&highlight=catfood+quality").  If you know what you are looking for, then you can find it.

---

