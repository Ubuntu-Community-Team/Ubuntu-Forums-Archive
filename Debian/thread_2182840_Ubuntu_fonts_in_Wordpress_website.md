---
title: "Ubuntu fonts in Wordpress website"
date: 2013-10-22
forum: Debian
---

### Post by Vic_Vartanian on 2013-10-22
Hi Guys,
I am a total newbie developer and even newer to Ubuntu. I have looked everywhere to find a way to post this question and found nothing. Maybe you guys can help? My question is... I am working on a website using Wordpress, however I noticed the theme uses Ubuntu font as well and not sure why? Is it necessary to add to all sites? or maybe just this one? I had never heard of Ubuntu until that point. On the CSS style.css for the theme Ubuntu is used in these ways...
@font-face {
    font-family: 'ubuntu';
    src: url('fonts/ubuntu-regular-webfont.eot');
    src: url('fonts/ubuntu-regular-webfont.eot?#iefix') format('embedded-opentype'),
         url('fonts/ubuntu-regular-webfont.woff') format('woff'),
         url('fonts/ubuntu-regular-webfont.ttf') format('truetype'),
         url('fonts/ubuntu-regular-webfont.svg#ubuntu') format('svg');
    font-weight: normal;
    font-style: normal;


}

AND.....

h1, h2, h3, h4, h5, h6 {


	font-family: ubuntu, "trebuchet ms",arial,helvetica;
}

Why add Ubuntu? confused. Please someone, anyone, school me on this! :)

---

### Post by Danny_Michel on 2013-10-22
Your question is not only in the wrong forum on this website, but it's on the wrong website.
Nonetheless, you dont NEED to use that font on your site.
What you're seeing there is how the theme developer used font-face to embed the Ubuntu font so you can use ```
font-family:ubuntu;
``` Just delete what you posted above, and replace any instances of 'ubuntu' with Helvetica or something.

*Can someone please move his post and my reply somewhere else?*

---

### Post by Vic_Vartanian on 2013-10-22
Thank you so much! Do I need to remove and replace it with my choice font from both examples or which one? 
Which site and/or formu do you recommend? I have looked everywhere! Thanks again!:KS

---

### Post by Danny_Michel on 2013-10-22
[http://www.cre8asiteforums.com/forums/](http://www.cre8asiteforums.com/forums/)

---

### Post by coffeecat on 2013-10-22
@Vic_Vartanian, I've moved your posts + the helpful replies from Danny_Michel into their own thread in a more suitable section, although no sub-forum in this site really caters for issues in Wordpress unless you are running Ubuntu as the underlying operating system. I've also renamed the thread to something more suitable.

Good luck with finding help, but please be aware that thread hijacking is frowned on in most forums.

**EDIT**: doesn't Wordpress itself have its own forum?

---

### Post by buzzingrobot on 2013-10-22
@Vic:  When a user visits a site, the browser can display texts only in fonts that are available to it.  I.e., on that user's machine.  The person who built that Wordpress theme included specifcations in the CSS (that @font_face construction) to load the fonts.  It says, "src: url('fonts/ubuntu-regular-webfont.eot')" which says the fonts are located locally in a "fonts" directory.  I.e., the theme developer included the fonts with the theme.

---

### Post by Vic_Vartanian on 2013-10-22
Danny, Thank you!

CoffeeCat, Thank you as well, and please accept my apologies. I had no idea that I "Hijacked" a forum. Although I am working on wordpress, this was indeed a Ubuntu related question, and given the limited search results I found this was indeed the best place on the web I could find. I will do my best to avoid making the same mistake, however this was not the type of question that would have been answered on WP forums. 

What is this site/forum for specifically? I am interested in knowing more about what Ubuntu is..

---

### Post by Vic_Vartanian on 2013-10-22
@buzzingbot --> What if I am using fonts from google that are rendered online from google.com/fonts? Does that eliminate the need for this altogether?

---

### Post by coffeecat on 2013-10-22
@Vic_Vartanian, I'll answer the questions you posed specifically to me and then step back so that others can help you with the font embedding issue which seems to be the core of your question.

> **Vic_Vartanian said:**
>  I had no idea that I "Hijacked" a forum.

It was a thread, not a forum you hijacked. Hijack is rather a strong word but understood on most forums and I had to use it in order to give you a friendly word of advice about forum etiquette, since you might be using other forums. In essence, a thread is a conversation started by the OP (original poster). In a support forum it is a request for help and others post their responses. If someone then comes along and posts their own question on someone else's thread, especially if it is not relevant to the thread topic, this distracts from help given to the OP, can derail the thread discussion and royally annoys some people. Hence the word. We pride ourselves on having a friendly forum here, but on others you might get a more - um - *robust* response. :)

> **Vic_Vartanian said:**
> however this was not the type of question that would have been answered on WP forums.

Are you sure about that? A simple search for embedded+font in the Wordpress forum revealed quite a number of threads:

[http://wordpress.org/search/embedded+font?forums=1](http://wordpress.org/search/embedded+font?forums=1)

It doesn't matter that your question is about the Ubuntu font. The principle is the same
> **Vic_Vartanian said:**
> What is this site/forum for specifically? I am interested in knowing more about what Ubuntu is..

Ubuntu is a free and open source operating system based on the Linux kernel, which comes in desktop and server versions:

[http://www.ubuntu.com/](http://www.ubuntu.com/)

This forum is the official forum for Ubuntu, but the members, staff included, are all volunteers, mostly ordinary users who just like giving help to others using Ubuntu. Have a look around the forum - you'll get a better idea of the sort of things discussed here, and good luck with your specific question. Quite a few people here have experience of Wordpress whether on their home servers or a hosting service, so you'll get good advice here.

---

