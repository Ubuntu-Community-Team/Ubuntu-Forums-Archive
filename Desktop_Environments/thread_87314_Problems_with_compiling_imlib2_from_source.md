---
title: "Problems with compiling imlib2 from source?"
date: 2005-11-07
forum: Desktop Environments
---

### Post by erik-the-red on 2005-11-07
I downloaded imlib2-1.2.1 from the Sourceforge.

./configure had no problems.

Make had a lot of errors.

```

api.c:30:22: error: ft2build.h: No such file or directory
api.c:31:10: error: #include expects "FILENAME" or <FILENAME>
In file included from api.c:40:
font.h:3:10: error: #include expects "FILENAME" or <FILENAME>
font.h:4:10: error: #include expects "FILENAME" or <FILENAME>
In file included from api.c:40:
font.h:43: error: syntax error before 'FT_Face'
font.h:43: warning: no semicolon at end of struct or union
font.h:43: warning: no semicolon at end of struct or union
font.h:45: warning: data definition has no type or storage class
font.h:53: error: syntax error before '}' token
font.h:57: error: syntax error before 'FT_Glyph'
font.h:57: warning: no semicolon at end of struct or union
font.h:58: warning: data definition has no type or storage class
font.h:101: error: syntax error before 'FT_UInt'
make[3]: *** [api.lo] Error 1
make[3]: Leaving directory `/home/alex/imlib2-1.2.1/src/lib'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/alex/imlib2-1.2.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/alex/imlib2-1.2.1'
make: *** [all-recursive-am] Error 2

```

What's up? I'd like to be able to compile Enlightenment 0.16.7. The apt repositories only have 0.16.6.

This is not E17, by the way.

---

### Post by Ampersand on 2005-11-07
Possibly a lack of freetype? Make sure you've got libfreetype6 and libfreetype6-dev (along with everything listed under imlib2 here: [http://www.get-e.org/User_Guide/English/_pages/2.1.html](http://www.get-e.org/User_Guide/English/_pages/2.1.html)).

---

### Post by erik-the-red on 2005-11-07
I definitely did not have FreeType2, which did not allow me to compile imlib2. I compiled FreeType2, and then I successfully compiled imlib2.

Now, enlightenment compilation is acting up.

```

draw.c:1280:36: error: X11/bitmaps/flipped_gray: No such file or directory
draw.c:1281:28: error: X11/bitmaps/gray: No such file or directory
draw.c:1282:29: error: X11/bitmaps/gray3: No such file or directory
draw.c: In function &#8216;DrawEwinShape&#8217;:
draw.c:1358: error: &#8216;flipped_gray_bits&#8217; undeclared (first use in this function)
draw.c:1358: error: (Each undeclared identifier is reported only once
draw.c:1358: error: for each function it appears in.)
draw.c:1359: error: &#8216;flipped_gray_width&#8217; undeclared (first use in this function)draw.c:1359: error: &#8216;flipped_gray_height&#8217; undeclared (first use in this function)
draw.c:1361: error: &#8216;gray_bits&#8217; undeclared (first use in this function)
draw.c:1361: error: &#8216;gray_width&#8217; undeclared (first use in this function)
draw.c:1362: error: &#8216;gray_height&#8217; undeclared (first use in this function)
draw.c:1364: error: &#8216;gray3_bits&#8217; undeclared (first use in this function)
draw.c:1364: error: &#8216;gray3_width&#8217; undeclared (first use in this function)
draw.c:1365: error: &#8216;gray3_height&#8217; undeclared (first use in this function)
make[3]: *** [draw.o] Error 1
make[3]: Leaving directory `/home/alex/enlightenment-0.16.7.1/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/alex/enlightenment-0.16.7.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/alex/enlightenment-0.16.7.1'
make: *** [all] Error 2

```

Am I missing some image library?

---

### Post by Ampersand on 2005-11-08
Have you got xlibs-dev?

Have a look through the output from configure (either in the terminal after running it, or in the config.log file in the enlightenment source directory) and see whether there are any libraries it couldn't find.

If this doesn't work, you might have more success on the forums at [http://www.edevelop.org](http://www.edevelop.org), or if you use IRC, #e on irc.freenode.net.

---

