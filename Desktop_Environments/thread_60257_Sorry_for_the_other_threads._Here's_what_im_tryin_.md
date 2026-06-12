---
title: "Sorry for the other threads. Here's what im tryin to say actually"
date: 2005-08-27
forum: Desktop Environments
---

### Post by ubuntu01 on 2005-08-27
Kumbuntu doesnt really suck, it just makes me crazy because:

I cant set my resolution to 1280x1024 at 85 Hz but in windows i can easily, fast, friendly, consistantly, and productively. Can u show me how exactly i can set it up?..

 :-|

---

### Post by bored2k on 2005-08-27
[QUOTE=ubuntu01]Kumbuntu doesnt really suck, it just makes me crazy because:

I cant set my resolution to 1280x1024 at 85 Hz but in windows i can easily, fast, friendly, consistantly, and productively. Can u show me how exactly i can set it up?..

 :-|[/QUOTE]
 And we're supposed to guess this from a " LINUX NEEDS TO BE WINDOWS" thread and another one where said you already quit and went for College Linux ? And since when is a Community Chat used for video resolution problems ?

These type of threads and attitudes dont make anyone happier nor friendlier at all.

[CENTER]**What is this distribution you're running? I've never heard of it.**[/CENTER]
Please read the FAQ [http://www.ubuntuforums.org/faq.php?](http://www.ubuntuforums.org/faq.php?)
> When asking for technical support:

   1. **Try to give information in the title of your post,** instead of using a title like “it's broken,” use a title that is specific, such as, “Unable to get sound to play in Firefox.” A clear title will attract more views to your thread, as it gives a clear indication of the content of the post to the people that are willing to help you. Ultimately this will allow you to get more help of a better quality. 
>     *  Please try to write your posts in English. We have many users from many different countries that visit here.
    * When writing a post, please space paragraphs with a blank line in between them for better readability.
    * Please do not write posts in all uppercase letters, as it looks as if you are screaming at the people reading your post.
    * Please refrain from using “leet” speak or slang. These forums are a tool for communication, which will be obfuscated by those types of writing.
    * Please do not shorten your words to acronyms or abbreviations. It is very difficult to read and understand.

---

### Post by sapo on 2005-08-27
[QUOTE=ubuntu01]Kumbuntu doesnt really suck, it just makes me crazy because:

I cant set my resolution to 1280x1024 at 85 Hz but in windows i can easily, fast, friendly, consistantly, and productively. Can u show me how exactly i can set it up?..

 :-|[/QUOTE]
 Jusn an advice:

If you are going to compare every single problem that you have in linux with windows, where you do can do it easily, fast, friendly, snsistantly, and productively, please dont waste your time and dont make us waste ours helping you and go back to windows at once!. [img]http://ubuntuforums.org/images/smilies/eusa_naughty.gif[/img]

To change your resolution you need to edit a text file and you have to know theHorizontal Sync and Vertical Refresh of you monitor (you can find it at google or in the manual of you monitor)

To change the resolution do it:

Open a Terminal and type:
```
sudo gedit /etc/X11/xorg.conf
```

Find this section:

```
Section "Monitor"
        Identifier      "710E"
        Option          "DPMS"
        HorizSync       30-71
        VertRefresh     50-160
EndSection

```

change the following lines to your values:

```
        HorizSync       30-71
        VertRefresh     50-160
```

then find the following line:

```
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection

```

Or whatever the resolution is.. but the Depth 24 is what matters...

Change it to your resolution... save the file and press Ctrl + Alt + Backspace to restart X

Then IF your monitor support this resolution you should get it with the refresh rate you mentioned.

---

### Post by Adrenal on 2005-08-27
Or System/Preferences/Screen Resolution
By the way, its spelt Kubuntu
Say it with me, Ku-boon-too
Good

---

