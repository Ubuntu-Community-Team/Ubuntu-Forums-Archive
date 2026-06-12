---
title: "Freedoom and Yadex"
date: 2012-04-06
forum: Gaming &amp; Leisure
---

### Post by Man with Hat on 2012-04-06
I'm still quite a newb at all of this. Years of MS windows sometimes confuses my poor little head with Linux. 

I've downloaded yadex so that I can play around with Freedoom, both are available in software centre. I tried to follow the instructions laid out. But I may have done something wrong. During the make process I have had to change a couple of pathnames in the GNU makefile and download lib headers for x11 and now I have gotten to a strange end. I get this error:

```
g++ -c -Iatclib -Iboost -I/usr/X11R6/include -O src/geom.cc -o obj/0/geom.o
g++ -c -Iatclib -Iboost -I/usr/X11R6/include -O src/gfx.cc -o obj/0/gfx.o
src/gfx.cc:313:6: error: #elif with no expression
make: *** [obj/0/gfx.o] Error 1

```What do I look for to change? I assume I just need to give something a value of 1, but what is it? Is it in the GNU makefile? I'm not really sure what I am doing :???:

I'm using 11.10 64bit version

BTW these are from GNU makefile, the only parts I could find with elif
```
cache/uptodate: scripts/youngest $(SRC_NON_GEN)
    @mkdir -p cache
    @if perl -v >/dev/null 2>&1; then                \
      echo Generating cache/srcdate;                \
      scripts/youngest $(SRC_NON_GEN) >cache/srcdate;        \
      touch -t `date '+%m%d'`0000 cache/srcdate;            \
    elif [ -r cache/srcdate ]; then                    \
      echo Perl not available. Keeping old cache/srcdate;        \
    else                                \
      echo Perl not available. Creating bogus cache/srcdate;    \
      date '+%Y-%m-%d' >cache/srcdate;                \
    fi
    @touch $@;

``````
cache/pixlist: $(DOC2_SRC_HTML)
    @echo Generating $@
    @mkdir -p cache
    @if perl -v >/dev/null 2>/dev/null; then            \
      perl -ne '@l = m/<img\s[^>]*src="?([^\s">]+)/io;        \
        print "@l\n" if @l;' $(DOC2_SRC_HTML) | sort | uniq >$@;    \
    elif [ -f $@ ]; then                        \
      echo "Sorry, you need Perl to refresh $@. Keeping old $@.";    \
    else                                \
      echo "Sorry, you need Perl to create $@. Creating empty $@.";    \
      touch $@;                            \
    fi

```

---

### Post by DoktorSeven on 2012-04-07
It's in src/gfx.cc

Line 313 should be #else instead of #elif.  That's not the only issue, however -- code is quite old and probably needs a lot of work to make runnable.

---

### Post by Man with Hat on 2012-04-07
Thanks for that, I have altered the line and gotten a little further in the "make."

I know basically nothing about code, would you (or anyone) be interested in telling me what I need to fix each time an error comes up if I post it? Or is that a really big ask? I get that other people have lives too.

Latest error:

```
src/wadlist.cc:178:18: note: candidate is:
/usr/include/c++/4.6/bits/stl_list.h:124:12: note: std::_List_iterator<boost::shared_ptr<Wad_file> >& std::_List_iterator<boost::shared_ptr<Wad_file> >::operator=(const std::_List_iterator<boost::shared_ptr<Wad_file> >&)
/usr/include/c++/4.6/bits/stl_list.h:124:12: note:   no known conversion for argument 1 from &#8216;int&#8217; to &#8216;const std::_List_iterator<boost::shared_ptr<Wad_file> >&&#8217;
make: *** [obj/0/wadlist.o] Error 1
```

---

