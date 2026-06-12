---
title: "fonts problem"
date: 2011-11-30
forum: Desktop Environments
---

### Post by tapas_mishra on 2011-11-30
This is an issue I wanted to report on forum here Chromium and Chrome both the browsers.On 11.04.

[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/856736](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/856736)
When I try to view websites in local languages in Chrome on Ubuntu 11.04
 then the font is not rendered correctly.Where as if I open the same website in Firefox then the site is being displayed without any problem
Here is a snapshot of the page in problem.
[https://picasaweb.google.com/mightydreams/HindiFontsProblem](https://picasaweb.google.com/mightydreams/HindiFontsProblem)
Here is the page in problem on Chrome
[https://picasaweb.google.com/mightydreams/HindiFontsProblem#5655127655183416498](https://picasaweb.google.com/mightydreams/HindiFontsProblem#5655127655183416498)
 A Correctly rendered page should appear like this
 [https://picasaweb.google.com/mightydreams/HindiFontsProblem#5655127704627761410](https://picasaweb.google.com/mightydreams/HindiFontsProblem#5655127704627761410)


[LEFT]I do not have a custom .fonts file.
Following are the sites which you can open

1) [http://in.jagran.yahoo.com/](http://in.jagran.yahoo.com/)
 2) [http://aajtak.intoday.in/story.php/content/view/68511/13/0](http://aajtak.intoday.in/story.php/content/view/68511/13/0)
 3) [http://aajtak.intoday.in/story.php/content/view/68513/13/0](http://aajtak.intoday.in/story.php/content/view/68513/13/0)
 4) [http://epaper.livehindustan.com/PUBLICATIONS/HT/HT/2010/11/20/index.shtml](http://epaper.livehindustan.com/PUBLICATIONS/HT/HT/2010/11/20/index.shtml)
                 5) [http://vadicjagat.com/?p=1043&utm_source=feedburner&utm_medium=email&utm_campaign=Feed%3A+vadicjagat%2FrUIj+%28Vadicjagat.com%29]("http://vadicjagat.com/?p=1043&utm_source=feedburner&utm_medium=email&utm_campaign=Feed%3A+vadicjagat%2FrUIj+%28Vadicjagat.com%29")
 6) [http://www.jitu.info/merapanna/?p=148](http://www.jitu.info/merapanna/?p=148)
 7) [http://vadicjagat.com/?p=1050&utm_source=feedburner&utm_medium=email&utm_campaign=Feed%3A+vadicjagat%2FrUIj+%28Vadicjagat.com%29](http://vadicjagat.com/?p=1050&utm_source=feedburner&utm_medium=email&utm_campaign=Feed%3A+vadicjagat%2FrUIj+%28Vadicjagat.com%29)
8) [http://ramayan.wordpress.com/](http://ramayan.wordpress.com/) and [http://ramayan.wordpress.com/goswami](http://ramayan.wordpress.com/goswami) 


The list of such sites is long.I also noticed if you are subscribed to any of the sites in local language on Facebook etc then the news feed on your wall which appears in chrome is distorted.Where as same thing appears correctly if you open the same thing in firefox.


Some how I am able to get the site working in both Chromium,Google-Chrome,Firefox 

by deleting following

```
 /usr/share/fonts/truetype/freefont/FreeSerif.ttf
 /usr/share/fonts/truetype/freefont/FreeSans.ttf

```which were installed by default. Can some one help to understand why did deleting above fonts worked and the sites started appearing correctly because I did not installed these fonts they were installed by default and many users suffer from this problem but every one would not have the idea to delete the above 2 fonts.Even I had searched more than six months on internet before I deleted above files to get things working correctly on my machine.


        

[/LEFT]

---

### Post by bluexrider on 2011-11-30
I am trying to read all of your post and I know that it is of importance but it is confusing as to what you are really asking? 

The statement is Firefox works but Chromium and Chrome both have issues?

so you are making a comparison fo the fonts that are displayed correctly as to help us.


I really have to say thank you cause a lot of work went into that.

---

### Post by tapas_mishra on 2011-11-30
I am trying to say following

Upon doing a fresh Ubuntu install open the above sites in chrome on a Ubuntu machine the sites will appear distorted,end user will not be able to read if he uses chrome or chromium as his browser.But if he used firefox as his browser then the same pages which appear incorrectly in chromium (default from Ubuntu) those pages will appear correct.

Now the end user posts his problem on forums,irc, etc etc.. finally he after 6 months come to know that if he deletes 2 fonts 

```
 /usr/share/fonts/truetype/freefont/FreeSerif.ttf
 /usr/share/fonts/truetype/freefont/FreeSans.ttf
```
which come on installation CD then this problem is solved.

In my case this problem is solved.But there will be many Ubuntu users who will not be aware that 2 default fonts are causing this problem,so it is important for Ubuntu developers to have a look at this.

What I want to convey by posting here the above links:- 

1) If some one on this list is aware of the development team which looks for chromium,fonts pass this thread as message to them.(I know Ubuntu developers read launchpad since I have been able to find a fix to this so it is more important for this to be passed) 

2) What are the steps which  I  can take to investigate as why the presence of fonts 
```
 /usr/share/fonts/truetype/freefont/FreeSerif.ttf
 /usr/share/fonts/truetype/freefont/FreeSans.ttf
```

created this problem because by default an end user who installs Ubuntu will never be able to know that presence of some default font which comes in installation CD caused the problem (distorted appearance of web sites in Indian Language Hindi,Tamil and other Indian languages).

Since the pages do appear distorted if I viewed the web pages in chrome but the pages appear correctly in firefox.If the default fonts were present.Now since I do have a solution I want to investigate/triage this bug further as what had caused it.
So I need suggestion to triage this bug given the fact that I found a **solution/hack/work around **(which is to delete those 2 fonts) but  what was the reason for this problem to come.
Or give me right link where I can interact with development team which looks after this kind of thing they will understand better.

Hope I made myself clear if not post I will reply.

---

