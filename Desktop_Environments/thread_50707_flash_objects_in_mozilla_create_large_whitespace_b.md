---
title: "flash objects in mozilla create large whitespace block."
date: 2005-07-21
forum: Desktop Environments
---

### Post by gammyhand on 2005-07-21
I am having problems with a lot of flash adverts in mozilla...you know the type. You rollover and they expand...well the problem is that when I load a webpage the first time I get a coloured block of the size that the expanded advert would be and it covers the page content. I have to reload the page again to get a normal view. Any ideas?

---

### Post by Phixion on 2005-07-21
[QUOTE=gammyhand]I am having problems with a lot of flash adverts in mozilla...you know the type. You rollover and they expand...well the problem is that when I load a webpage the first time I get a coloured block of the size that the expanded advert would be and it covers the page content. I have to reload the page again to get a normal view. Any ideas?[/QUOTE]

Hi there, have you installed the plugin for flash?

sudo apt-get install flashplayer-mozilla

---

### Post by gammyhand on 2005-07-21
Yes....the problem is not that flash is not loading, it is that the advert is not hiding its hidden content basically.

---

### Post by alegomes on 2005-07-21
[QUOTE=gammyhand]Yes....the problem is not that flash is not loading, it is that the advert is not hiding its hidden content basically.[/QUOTE]

Sometimes I have the same problem.

---

### Post by gammyhand on 2005-07-21
[QUOTE=alegomes]Sometimes I have the same problem.[/QUOTE]
 I am guessing you have not got round it either :)

---

### Post by graigsmith on 2005-07-21
i have a work-around this. make a new firefox bookmark with this as the link, just copy and paste it. once you have that in there. click this, and it will run that javascript, and create links to all of those flash documents.  once they are out of the page, you should be able to use the flash piece.  some guy from the forums told me this before, so its not my idea.  


```
javascript:s='';b=0;while(document.embeds[b]){s+='<a href=%22'+document.embeds[b].src+'%22>'+document.embeds[b].src+'</a><br>';b++;};if(s){document.write(s);document.close();}  else{alert('Sorry, no embeds found.');}
```

---

### Post by gammyhand on 2005-07-21
> **graigsmith]i have a work-around this. make a new firefox bookmark with this as the link, just copy and paste it. once you have that in there. click this, and it will run that javascript, and create links to all of those flash documents.  once they are out of the page, you should be able to use the flash piece.  some guy from the forums told me this before, so its not my idea.  


```
javascript:s='' said:**
> ){s+='<a href=%22'+document.embeds[b].src+'%22>'+document.embeds[b].src+'</a><br>';b++;};if(s){document.write(s);document.close();}  else{alert('Sorry, no embeds found.');}
```
 That's not really my idea of a workaround sorry. I was hoping for something seamless. Thanks for your effort though, it's appreciated :)

---

### Post by smackmandoo on 2007-08-14
I have the same problem and have started using the Epiphany web browser. Seamless

---

