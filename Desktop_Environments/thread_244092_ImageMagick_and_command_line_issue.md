---
title: "ImageMagick and command line issue"
date: 2006-08-25
forum: Desktop Environments
---

### Post by mediocre on 2006-08-25
I want to pop a "fortune cookie" onto my desktop wallpaper. Eventually, something like this, but with full path information, will appear in my rc.local file, where w.png is the "blank" wallpaper and w2.png is my wallpaper.

But, there must be a better way. The trouble with this is that depending on the contents of the fortune cookie, some bad things can happen. For instance, if the fortune contains a quotation mark or apostrophe, or certain combinations of letters, these get treated, apprarently, as commands or delimiters. I just want whatever fortune emits to be treated as text. Anyone want to take a stab at what I'm doing wrong?

```
convert w.png  -fill yellow -pointsize 30 -draw "text 50,50 '$(fortune -a)'" w2.png
```

Thanks,

Nick.

---

### Post by biocrasher on 2006-08-26
That's a very nice idea :KS  .

To make it work correctly you can do something like this 
```
convert orig_w.png  -fill black   -pointsize 30   -draw "text 50,50     \"$(fortune|sed -e ' s/\"/\\\"/g' )\"    " result.png
```

If you look, the only difference is that I'm quoting the whole thing
and make sure to escape any double quotes that may lie within it.

I've run it in an loop for quite some time and didn't have problems,
except one. The size of the box is sometimes too small for the text,
so it doesn't get rendered correctly. You may have to make it bigger,
since fortune sometimes spits whole essays.:)

You can also make a script to keep it changing, like

```
while (test 1==1) do
    sleep 15m ;
    convert orig_w.png  -fill black   -pointsize 30   -draw "text 50,50     \"$(fortune|sed -e ' s/\"/\\\"/g' )\"    " result.png   ;
done
```

(It won't change immediatetly ,but, at least in KDE, a virtual desktop switch triggers a wallpaper redraw)

---

### Post by mediocre on 2006-08-26
Excellent--thank you very much for that. I notice that what appear to be TAB characters in the original fortune seem to come out wonky... as left parentheses it seems. Not knowing the sed syntax, I'm wondering if I should just add a \t to that group of characters.

Nick.

---

### Post by biocrasher on 2006-08-26
In that case you can do this :
```
convert orig_w.png  -fill black   -pointsize 30   -draw "text 50,50     \"$(fortune|sed -e ' s/\"/\\\"/g  ;   s/\t/\ \ \ \ /g' )\"
```

You can keep adding substitute commands, the syntax is easy:
> s/regular_expression/modified_expression/**g** 

Remember to separate them with semicolons and
add the **g** to their end, or else the change happens 
only on the first incidence of the regular expression.

---

### Post by fakie_flip on 2006-08-26
I tried it out, and it works nice, but how long does it take for the wallpaper to redraw? Is there a command that can be added to the while loop that will redraw the wallpaper?

---

