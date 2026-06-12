---
title: "Selected (highlighted) area changes upon color change"
date: 2013-05-10
forum: Forum Feedback &amp; Help
---

### Post by Doug S on 2013-05-10
I have only experienced this issue with the new version of the forums.
It only occurs rarely, and I have not determined any magic sequence.

When making forum posts, it is very typical that I will change the color of some selected text so as to emphasize it, and draw attention to it, within a larger provided context. After I have selected the desired text area, I move the cursor over to the "Text Color" button and then "click" to change the color (or open the pull down menu to select the color, if it is my first change). Sometimes (rarely) the text that changes color is not exaxtly what I have selected. Sometimes the first two characters do not change color. Other times the entire selection moves over two characters. If I try to go back and change the unchanged characters they never will change, the change always move right two characters. In the example of the attached screen shots, I was able to finally get the desired characters to change by selecting an extra few characters to the left also, and then changing them back afterwards. Also in this example, the added two characters at the right were the "[" and "\" of a closing code tag, which then messed up the code tags, which I figured out during "Preview Post".

This is better described by screen shots: First, text selected and cursor hovering over the "text color" button (cursor does not appear in screen shots); Second, the cursor is still hovering over the "text color" box, but after I have "clicked", notice the highlight has shifted two characters to the right; Third I moved the cursor to somewhere over a clear area in the text box and "clicked" so as to remove the highlighting, notice the text that turned [COLOR=#ff0000]red [/COLOR]is not what I originally wanted; Fourth, is just from when I was trying to include extra characters so as to get what I really wanted.

[ATTACH=CONFIG]242436[/ATTACH] [ATTACH=CONFIG]242437[/ATTACH] [ATTACH=CONFIG]242438[/ATTACH] [ATTACH=CONFIG]242439[/ATTACH]

If, I can find them again, I'll come back and edit this post with links to other examples.

I tend to only use ubuntu server editions, so this type of work is done via a windows vista computer with IE version 9.0.8112.16421

Edit: Add Links to other examples:
[http://ubuntuforums.org/showthread.php?t=2127604&p=12566433#post12566433](http://ubuntuforums.org/showthread.php?t=2127604&p=12566433#post12566433)  [COLOR=#FF0000]<<< Really good example, because other almost identical lines worked fine.[/COLOR]
[http://ubuntuforums.org/showthread.php?t=2126317&p=12561779#post12561779](http://ubuntuforums.org/showthread.php?t=2126317&p=12561779#post12561779)

---

### Post by matt_symes on 2013-05-11
Hi 

If you switch off editor and onto basic formatting what do you see ?

Click the a/A button on the top left.

I had an issue with URL's once or twice and it happened just a minute ago. 

Looking at the basic formatting i was able to see that all my text i was writing after i had copied and pasted a url was still be included inside the bbl [noparse][URL][/noparse] tag and so was being coloured and underlined.

Kind regards

---

### Post by Doug S on 2013-05-11
> **matt_symes said:**
> Hi 
If you switch off editor and onto basic formatting what do you see ?
Click the a/A button on the top left.Hi Matt,
It all looks normal in basic formatting mode. I looked at the example linked to above, where I added the comment "good example" and the color tag attributes are simply shifted. Although your suggestion does give me the, now obvious, thought of how to work around this issue when it occurs, by switching to basic formatting and just fixing it.

Actually, I'll copy a portion of the "good example" to below, via a plain text editor middle man, to sanitize, and see if the issue occurs again when I try to change some test colors.
As you can see the issue occured again, but not in the exact same spots. Weird.

```
doug@doug-64:~$ dig google.com
; <<>> DiG 9.8.1-P1 <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 20057
;; flags: qr rd ra; QUERY: 1, ANSWER: 11, AUTHORITY: 13, ADDITIONAL: 0
;; QUESTION SECTION:
;google.com.                    IN      A
;; ANSWER SECTION:
google.com.             [COLOR=#FF0000]198   [/COLOR]  IN      A       173.194.33.0
google.com.             [COLOR=#FF0000]198[/COLOR]     IN      A       173.194.33.1
google.com.             [COLOR=#FF0000]198[/COLOR]     IN      A       173.194.33.2
google.com.             [COLOR=#FF0000]198[/COLOR]     IN      A       173.194.33.3
google.com.             [COLOR=#FF0000]198[/COLOR]     IN      A       173.194.33.4
google.com.             19[COLOR=#FF0000]8  [/COLOR]   IN      A       173.194.33.5
google.com.             [COLOR=#FF0000]198[/COLOR]     IN      A       173.194.33.6
google.com.             [COLOR=#FF0000]198[/COLOR]     IN      A       173.194.33.7
google.com.             [COLOR=#FF0000]198 [/COLOR]    IN      A       173.194.33.8
google.com.             [COLOR=#FF0000]198[/COLOR]     IN      A       173.194.33.9
google.com.             19[COLOR=#FF0000]8  [/COLOR]   IN      A       173.194.33.14
;; AUTHORITY SECTION:
.                       323144  IN      NS      k.root-servers.net.
...[deleted]...
.                       323144  IN      NS      g.root-servers.net.
;; Query time: 36 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Wed Mar 20 12:01:47 2013
;; MSG SIZE  rcvd: 415

```

---

### Post by matt_symes on 2013-05-11
Hi
DougS - You've broken the forums :lolflag:

I have no idea what is causing that. You would have thought using a plain text editor - good move btw -  would have removed any special formatting.

The editor has caused some people some problems though, and they're generally on Windows using Internet Explorer.

Kind regards

---

### Post by Doug S on 2013-05-12
> **matt_symes said:**
> You would have thought using a plain text editor - good move btw -  would have removed any special formatting.It did remove all special formatting. Then, after I pasted it above I re-did the highlighting and change color thing 11 times, once for each "198". While the issue occured again, it did it in not the exact same places as the original posting. Sorry, if my earlier post was unclear.

---

### Post by Doug S on 2013-05-12
> **matt_symes said:**
> The editor has caused some people some problems though, and they're generally on Windows using Internet Explorer.I did an experiment:
Step 1: Download and install the Firefox web browser.
Note 1:Many replies to this thread were done in the below steps, never with the intent to "Submit Reply", but as tests. And always with the good test segment of text as per my previous post.
Step 2: Use MS IE (Microsoft Internet Explorer) and try to change the color of the 11 "198"s as before. 6 times it did not work properly.
Step 3: Use FF (Firefox) and try to change the color of the 11 "198"s as before. 0 times it did not work properly.
Step 4: Use MS IE and try to change the color of  the 11 "198"s as before. 6 times it did not work properly (I do not know if the same 6 as before).
Step 5: Use FF and try to change the color of the 11 "198"s as before. 0 times it did not work properly.

Conclusion: It is (way past) time to switch web browsers.

---

