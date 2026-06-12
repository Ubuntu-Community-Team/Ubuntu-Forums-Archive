---
title: "Unable to Respond to a Post"
date: 2017-02-18
forum: Forum Feedback &amp; Help
---

### Post by norobro on 2017-02-18
Hello,
I recently joined the forum and have only made two posts: 
[https://ubuntuforums.org/showthread.php?t=2352464](https://ubuntuforums.org/showthread.php?t=2352464)  
[https://ubuntuforums.org/showthread.php?t=2349493](https://ubuntuforums.org/showthread.php?t=2349493)

I have been trying, intermittently, to respond to a post in Programming Talk for over 12 hrs. but always receive an error:> Forbidden - You don't have permission to access newreply.php on this server

Thanks.

---

### Post by wildmanne39 on 2017-02-18
We are having forum issues if you try now since they just stopped again you should be able to see the threads.

Moved thread to FF&H.

---

### Post by norobro on 2017-02-18
Thanks. I was able to post.

---

### Post by wildmanne39 on 2017-02-19
Your welcome!:)

---

### Post by norobro on 2017-03-30
Are there problems with the forum again? Or is it me?

Getting the same 403 error as in post #1.

Logged in with SSO.

---

### Post by yetimon_64 on 2017-03-31
> **norobro said:**
> Are there problems with the forum again? Or is it me?

Getting the same 403 error as in post #1.

Logged in with SSO.

Most likely it is the forum. Such issues, like the one you are experiencing, have been ongoing since about July last year. See [[COLOR=#0000ff]--this FF&H thread--[/COLOR]]("https://ubuntuforums.org/showthread.php?t=2331266") started by UF staff member bapoumba in July, the last post there is from only about a week ago so the problems still seem to be around.

Cheers, yeti.

---

### Post by cariboo on 2017-03-31
> **norobro said:**
> Are there problems with the forum again? Or is it me?

Getting the same 403 error as in post #1.

Logged in with SSO.

Could you let us know what thread you are trting to access.

---

### Post by norobro on 2017-03-31
Thanks for the replies.

I'm still unable to respond to this thread: [https://ubuntuforums.org/showthread.php?t=2357111](https://ubuntuforums.org/showthread.php?t=2357111)

---

### Post by Doug S on 2017-03-31
> **norobro said:**
> Thanks for the replies.

I'm still unable to respond to this thread: [https://ubuntuforums.org/showthread.php?t=2357111](https://ubuntuforums.org/showthread.php?t=2357111)Your inability to post on that thread is likely due to some specific content of your post. From the link within the original post you pointed to, my best wild guess is that you might have been attempting to include < H T M L > (without spaces) in your post (even inside of quote or code tags), which still results in the forbidden message. However, there are others strings that result in the forbidden message.

---

### Post by norobro on 2017-03-31
> **Doug S said:**
> Your inability to post on that thread is likely due to some specific content of your post. From the link within the original post you pointed to, my best wild guess is that you might have been attempting to include < H T M L > (without spaces) in your post (even inside of quote or code tags), which still results in the forbidden message. However, there are others strings that result in the forbidden message.Educated guess not wild guess! You're exactly right. I was trying to post a simple example to illustrate the OP's scope problem.

You learn something new every day.

So it was me. Thanks for the help!

---

### Post by Doug S on 2017-03-31
> **norobro said:**
> So it was me. Thanks for the help!It was not you at all. Such content, particularly within code tags, should work fine.

EDIT 1: Hmmm... that html code segment you were attempting to post in your reply reveals another string segment that doesn't work, that I didn't know about before:

```

<!DOCTYPE html>

< h t m l >
    <head>
        < m e t a charset="UTF-8">
        <link rel="stylesheet" type="text/css" href="test.css">
    </head>
    <body>
        <div class="list">
            <ul>
                <li>
                    <span class="list_counter">first list</span>
                </li>
            </ul>
            <ul> 
                <li>
                    <span class="list_counter">second list</span>
                </li>
            </ul>    
        </div> 
    </body>
</html>

```Notice how I had to also introduce spaces in the "meta" line to get this posting to actually post. (probably 1 space would have been enough)

EDIT 2: It is very very difficult to finds examples where this stuff used to work properly, because the search function gets broken with the same strings. However, I did find one example from June 2015. [https://ubuntuforums.org/showthread.php?t=2283053&page=2&p=13306531#post13306531]("https://ubuntuforums.org/showthread.php?t=2283053&page=2&p=13306531#post13306531")

---

### Post by norobro on 2017-03-31
Ah, I tried "< h t m l >" and got the same error so I went with the code site.

What is the purpose of not allowing those tags? 

I post some on LQ and those tags are allowed. A quick search yielded this: [http://www.linuxquestions.org/questions/programming-9/two-forms-why-linked-4175571685/](http://www.linuxquestions.org/questions/programming-9/two-forms-why-linked-4175571685/)

---

### Post by Doug S on 2017-03-31
> **norobro said:**
> Ah, I tried "< h t m l >" and got the same error so I went with the code site.

What is the purpose of not allowing those tags?As far as I am concerned they should work and they used to work. I believe, but have no proof, that their use got broken as an unintended side effect of the WAF (Web Application Firewall) that was either added or strengthened after the big hack last summer sometime. See also [here]("https://ubuntuforums.org/showthread.php?t=2331266&page=36&p=13617022#post13617022") and [here]("https://ubuntuforums.org/showthread.php?t=2331266&page=36&p=13620834#post13620834").

---

### Post by norobro on 2017-03-31
I missed your EDIT 2 above before posting.

That "Forbidden" error message is very informative ;)

I appreciate your help on this.

---

### Post by vasa1 on 2017-03-31
> **norobro said:**
> ...
What is the purpose of not allowing those tags? 
...
[https://en.wikipedia.org/wiki/Internet_forum#BBCode_and_HTML](https://en.wikipedia.org/wiki/Internet_forum#BBCode_and_HTML)

---

### Post by cariboo on 2017-04-01
HTML tags were found to be a way in for attackers, so they were disabled after the last Forum breach. If you need to post some HTML, use pastebin:

[https://paste.ubuntu.com/](https://paste.ubuntu.com/)

---

### Post by Doug S on 2017-04-01
> **cariboo said:**
> HTML tags were found to be a way in for attackers, so they were disabled after the last Forum breach. If you need to post some HTML, use pastebin.O.K. thanks for your reply. Even within code tags they were a problem? Do you know anything about the other strings I found, "HT TP/1.1" and "HT TP/1.0" (without the space), which are often part of log segments we want to post, typically within code tags.

---

