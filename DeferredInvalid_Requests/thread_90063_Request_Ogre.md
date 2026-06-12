---
title: "Request: Ogre"
date: 2005-11-14
forum: Deferred/Invalid Requests
---

### Post by polpak on 2005-11-14
MOTU guys said it's in Dapper universe now.. Can we get this backported? I find it much more preferable than crystalspace.

---

### Post by polpak on 2005-11-16
Hoping to drum up more support for this package...

Here's the url to their site so you can see what I'm talking about:

[http://www.ogre3d.org/](http://www.ogre3d.org/)

I'd really like to use this lib to make some nice 3d games under ubuntu.

Thanks

---

### Post by Azriphale on 2005-11-18
Anybody listening?

I have been having trouble getting the OGRE source from [www.ogre3d.org](www.ogre3d.org) to compile. I seriously need this package, to begin work on my engine, and to test various things i've been playing with in Blender. Please (please please please) can we get a backport?

Or perhaps point us in the direction of the source that was compiled on Dapper?

In the meanwhile, I am going to scratch around for my dependencies again, after a reinstall (after screwing with my '/usr/include's a little too much after the last time i tried OGRE [last night])

It did, however give me the chance I needed to re-arrange my filesystem.

---

### Post by Azriphale on 2005-11-18
I am likely beginning to break my Breezy install.

I added the following line to my /etc/apt/sources.list

deb [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper universe main restricted multiverse

I then asked synaptic to reload the package defs.

i'm now downloading ogre. The trouble is, it has to ubgrade a few packages to the version in dapper. This might break breezy. I'll post here when I know what happens. 

If it does break breezy, i'll add the dapper deb-src line to /etc/apt/sources.list and attempt to compile the libs for breezy. I'll also let you know what happens there.

I warn anybody against trying to add that dapper repo, as it may break things. We'll see.

---

### Post by Azriphale on 2005-11-18
Well, my machine didn't blow up. Good sign.

but now, i'm trying to compile a very simple ogre app. (from tutorial 1 on the Ogre wiki)

[http://www.ogre3d.org/wiki/index.php/Basic_Tutorial_1](http://www.ogre3d.org/wiki/index.php/Basic_Tutorial_1)

I get this garbage out

```

simon@Azriphale:~/ogretest$ g++ ogretest.cpp -I/usr/include/OGRE -I/usr/include/c++/4.0/ext


/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/bits/stl_tempbuf.h: In destructor &#8216;std::_Temporary_buffer<_ForwardIterator, _Tp>::~_Temporary_buffer()&#8217;:
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/bits/stl_tempbuf.h:129: error: &#8216;return_temporary_buffer&#8217; is not a member of &#8216;std&#8217;
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/bits/stl_tempbuf.h: In constructor &#8216;std::_Temporary_buffer<_ForwardIterator, _Tp>::_Temporary_buffer(_ForwardIterator, _ForwardIterator)&#8217;:
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/bits/stl_tempbuf.h:152: error: &#8216;get_temporary_buffer&#8217; was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/bits/stl_tempbuf.h:153: error: expected primary-expression before &#8216;>&#8217; token
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/bits/stl_tempbuf.h:161: error: &#8216;return_temporary_buffer&#8217; is not a member of &#8216;std&#8217;
/usr/include/c++/4.0/ext/algorithm: In function &#8216;bool __gnu_cxx::is_heap(_RandomAccessIterator, _RandomAccessIterator)&#8217;:
/usr/include/c++/4.0/ext/algorithm:445: error: &#8216;__is_heap&#8217; is not a member of &#8216;std&#8217;
/usr/include/c++/4.0/ext/algorithm: In function &#8216;bool __gnu_cxx::is_heap(_RandomAccessIterator, _RandomAccessIterator, _StrictWeakOrdering)&#8217;:
/usr/include/c++/4.0/ext/algorithm:466: error: &#8216;__is_heap&#8217; is not a member of &#8216;std&#8217;
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/bits/basic_string.tcc: In member function &#8216;typename std::basic_string<_CharT, _Traits, _Alloc>::size_type std::basic_string<_CharT, _Traits, _Alloc>::find(const _CharT*, typename _Alloc::size_type, typename _Alloc::size_type) const&#8217;:
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/bits/basic_string.tcc:718: error: &#8216;search&#8217; is not a member of &#8216;std&#8217;

```

huh???

I was having the same problem after compiling the ogre source from Debian unstable, and also the ogre-1.0.3 source. Do I need other include dirs for this GCC stl stuff to work? or is everything confused?

On the other hand, you can probably go ahead and fetch ogre from that dapper repository. It will say that it wants to upgrade some packages, let it do that (it requires the versions from dapper, which are one minor version up than those of breezy)

---

### Post by Azriphale on 2005-11-18
oooh. I'm an idiot.

The solution to all my remaining problems are found at the link below

[http://www.ogre3d.org/wiki/index.php/SettingUpAnApplication]("http://www.ogre3d.org/wiki/index.php/SettingUpAnApplication")

stupid stupid stupid
very stupid

anyway, it appears I have a working OGRE.

Now I can begin the real work.

If you need any help....

---

### Post by polpak on 2005-12-28
So is there any chance of seeing this before Dapper is released?

---

### Post by kudu on 2005-12-29
I don't know, I'm totally frustrated with trying to compile Ogre so the blighter will actually WORK! I sure hope we can get a package that puts it all together with one smooth click.

Please???

---

### Post by eyce on 2005-12-29
I understand that the core packages that make up any distro are release controlled - but I dont quite understand why the independant stuff is controlled under the release infrastructure :-/

---

### Post by kudu on 2005-12-30
[QUOTE=Azriphale]I am likely beginning to break my Breezy install.

I added the following line to my /etc/apt/sources.list

deb [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper universe main restricted multiverse

I then asked synaptic to reload the package defs.

i'm now downloading ogre. The trouble is, it has to ubgrade a few packages to the version in dapper. This might break breezy. I'll post here when I know what happens. 

If it does break breezy, i'll add the dapper deb-src line to /etc/apt/sources.list and attempt to compile the libs for breezy. I'll also let you know what happens there.

I warn anybody against trying to add that dapper repo, as it may break things. We'll see.[/QUOTE]


Broke mine! Bummer but mea culpa no doubt. Anyway, I have a fresh new Breezy install. :)

One thing though...if that's what dapper is gonna look like I'm sticking to Breezy. Everything looks so QTish.

Looks like I have to wait on Ogre...

kudu...out

---

### Post by jdong on 2006-01-02
Yes, I'll take a look at the package... Please be patient; if you read the sticky I have been on vacation over the holiday season.

---

### Post by jdong on 2006-01-02
make[4]: Entering directory `/home/jdong/ubp-compile-temp/ogre-1.0.6/build-tree/ogre-free/Samples/Common/CEGUIRenderer'
make[4]: *** No rule to make target `all'.  Stop.



Does not build.

---

### Post by kudu on 2006-01-05
[QUOTE=jdong]make[4]: Entering directory `/home/jdong/ubp-compile-temp/ogre-1.0.6/build-tree/ogre-free/Samples/Common/CEGUIRenderer'
make[4]: *** No rule to make target `all'.  Stop.



Does not build.[/QUOTE]

So where are we at with this ? As a matter of record I've gotten it to build, it just doesn't put all the files where they properly need to go and I'm not sure where they need to go. Hence a correctly setup package would be awesome!
Also, requires certain dependency stuff, like cg.

Ogre is definitely worth getting into ubuntu.

Regards,
kudu

---

### Post by fct on 2006-01-06
Here are detailed instructions to compile it on Breezy:

[http://www.games-creators.org/wiki/Installer_OGRE_sous_Ubuntu_Breezy](http://www.games-creators.org/wiki/Installer_OGRE_sous_Ubuntu_Breezy)

Although in french, the instructions are perfectly understandable, even looking just at the commands. And that's no guess, I used that guide to compile ogre successfully in one machine, use checkinstall to make packages and then install them in another machine.

But I'd prefer the backport instead of all the compiling drama. ;)

---

### Post by kudu on 2006-01-06
And this will put all the correct files where they need to go ?? So all one has to do is actually write some useable, "compileable" code ??

Oh I hope so!

kudu...out

er...merci boucoup for the link.  :D

---

### Post by fct on 2006-01-06
Nope, you'll still have to mess with the samples' skeleton files to start a working minimal project (mostly the Example*.h headers). But if you disregard the "--prefix=/home/..." thingie in the instructions I linked to, you can install the libraries system-wide (at /usr/local/lib). That way, I was able to compile with "g++ `pkg-config --libs --cflags OGRE` file.cpp".

And even then, you might run into problems if /usr/local/lib is not looked at by the linker (the binaries won't be able to find the library when run). I had to add the line "/usr/local/lib" to /etc/ld.so.conf and run ldconfig to get the compiled binary working.

That might be solved with "./configure --prefix=/usr", but I didn't want to mix the new files with the system ones, even if installed with checkinstall. Then again, perhaps I'm just being paranoid.

---

### Post by Bobuido on 2006-06-26
My friend told me about the wonderful project that is Ogre - It is sad to see it is not in the repositories

I think a lot of Ubuntu/Linux newbies, myself included, cringe at the thought of compiling code ourselves

Synaptic was one of the major selling points for me - Search > Mark > Install

It's this ease of use that the majority of us are so used to with Windows installers

So here it is  - My vote for an Ogre package

I'd also like to take the opportunity to thank all the people that work so hard to provide this packaging service for us

---

