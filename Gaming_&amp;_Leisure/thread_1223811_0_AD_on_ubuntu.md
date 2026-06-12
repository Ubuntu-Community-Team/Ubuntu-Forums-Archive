---
title: "0 AD on ubuntu?"
date: 2009-07-26
forum: Gaming &amp; Leisure
---

### Post by KhaaL on 2009-07-26
Since 0 AD went opensource, has anyone been succesful in running it on ubuntu? their howto page is [right here]("http://trac.wildfiregames.com/wiki/Playing0AD") for the curious.

---

### Post by PanCiasteczko on 2009-07-26
developers did


here are instructions step by step:

[http://trac.wildfiregames.com/wiki/BuildInstructions](http://trac.wildfiregames.com/wiki/BuildInstructions)

---

### Post by oldrocker99 on 2009-07-26
I followed the instructions on that link to the letter, and got a Big Pile O'Errors. Tiime to dig into the bug reports...

[Later] I just submitted a bug report. We'll see what happens.

:guitar:

---

### Post by Vadi on 2009-07-26
[http://www.playdeb.net/updates/?testing=Y#0ad](http://www.playdeb.net/updates/?testing=Y#0ad)

might need to login and switch to the testing version to get it though

---

### Post by meborc on 2009-08-13
> **Vadi said:**
> [http://www.playdeb.net/updates/?testing=Y#0ad](http://www.playdeb.net/updates/?testing=Y#0ad)

might need to login and switch to the testing version to get it though

don't see it any more... would like to try the game, but have been unable to build it correctly

when following the orders from the build page, the executable is not created... i guess i am missing some dependency :(

---

### Post by 569874123 on 2009-08-13
How to install: (warning it is in portuguese, use google translate or st :P)
[http://ubuntued.info/2009/08/0-a-d-um-jogo-de-estrategia-com-muito-potencial.html](http://ubuntued.info/2009/08/0-a-d-um-jogo-de-estrategia-com-muito-potencial.html)

---

### Post by meborc on 2009-08-13
> **569874123 said:**
> How to install: (warning it is in portuguese, use google translate or st :P)
[http://ubuntued.info/2009/08/0-a-d-um-jogo-de-estrategia-com-muito-potencial.html](http://ubuntued.info/2009/08/0-a-d-um-jogo-de-estrategia-com-muito-potencial.html)

thanks for the link, but it did not help... all goes well until the final make:

```
[QUOTE]==== Building pyrogenesis ====
Linking pyrogenesis
../../../binaries/system/liblowlevel_dbg.a(file_system.o): In function `boost::enable_if<boost::filesystem::is_basic_path<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >, bool>::type boost::filesystem::exists<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >(boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> const&)':
file_system.cpp:(.text._ZN5boost10filesystem6existsINS0_10basic_pathISsNS0_11path_traitsEEEEENS_9enable_ifINS0_13is_basic_pathIT_EEbE4typeERKS7_[boost::enable_if<boost::filesystem::is_basic_path<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >, bool>::type boost::filesystem::exists<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >(boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> const&)]+0x32): undefined reference to `boost::filesystem::detail::status_api(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, int&)'
../../../binaries/system/liblowlevel_dbg.a(file_system.o): In function `boost::enable_if<boost::filesystem::is_basic_path<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >, bool>::type boost::filesystem::is_directory<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >(boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> const&)':
file_system.cpp:(.text._ZN5boost10filesystem12is_directoryINS0_10basic_pathISsNS0_11path_traitsEEEEENS_9enable_ifINS0_13is_basic_pathIT_EEbE4typeERKS7_[boost::enable_if<boost::filesystem::is_basic_path<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >, bool>::type boost::filesystem::is_directory<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >(boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> const&)]+0x32): undefined reference to `boost::filesystem::detail::status_api(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, int&)'
collect2: ld returned 1 exit status
make[1]: *** [../../../binaries/system/pyrogenesis_dbg] Error 1
make: *** [pyrogenesis] Error 2

```

i guess the problem is in boost... should i purge libboost and try installing it again? anyone has any ideas?

---

### Post by Perfect Storm on 2009-08-13
There's two version of boost in 9.04, (diffrent version) you can try the other one.

---

### Post by meborc on 2009-08-13
```
make[1]: *** No rule to make target `/usr/include/boost/config/no_tr1/cmath.hpp', needed by `obj/network_Debug/NetServer.o'.  Stop.

```

it seems i still have problems... this is with libboost1.35-dev :(

i wish someone would get it built on 9.04 and give guidance :D

---

### Post by meborc on 2009-09-30
any luck?

if someone has build a deb for 9.10 karmic, i would be VERY glad :D

---

### Post by Bölvaður on 2009-09-30
> **meborc said:**
> any luck?

if someone has build a deb for 9.10 karmic, i would be VERY glad :D

:lolflag:

you might be glad and a little bit angry to know there has been a deb on playdeb for a "long time", but I bet it isn't as new as if you'd build the game from source today.

[http://wiki.getdeb.net/TestingRepository]("http://wiki.getdeb.net/TestingRepository")

I cannot say anything more, perhaps it doesnt work for you.

---

### Post by SupaSonic on 2009-10-04
I wish the instructions were a bit more detailed on the project's website. Sigh.

---

### Post by jkysam on 2009-10-05
[FONT=Lucida Sans Unicode][SIZE=2]I built the 0AD source on my 9.04 last week without much trouble and got it to run.

The instructions [here ]("http://trac.wildfiregames.com/wiki/BuildInstructions")are decent and pretty much all you need.

But anyway here are the steps I followed:

Check out the code:
```
svn co http://svn.wildfiregames.com/public/ps/trunk/ 0AD
```

Run the suggested apt-get:

```
sudo apt-get install build-essential libsdl1.2-dev zlib1g-dev libpng12-dev libjpeg62-dev libgamin-dev nasm libwxgtk2.8-dev libboost-dev libboost-signals-dev libboost-filesystem-dev libopenal-dev libalut-dev libvorbis-dev libogg-dev libcrypto++-dev binutils-dev libnspr4-dev libdevil-dev libenet-dev libxml2-dev
```

Maybe this is what most people are missing but in addition to those I also had to install:
```
sudo apt-get install pkg-config libboost-system1.37-dev
```

And finally
```
cd 0AD/build/workspaces
./update-workspaces.sh
cd gcc
make
```

That worked for me. 

And to run the game:
```
../../../binaries/system/pyrogenesis_dbg
```[/SIZE][/FONT]

---

### Post by meborc on 2009-10-06
for some reason it did not work for me... i guess my jaunty install is a bit "custom" so it might be something is conflicting with the dependencies

i DID manage to build it on karmic :D the difference being libboost version 1.38 instead of 1.37

nice game... now i need to see more development and bug fixing

---

### Post by SupaSonic on 2009-10-07
Managed to get it working on Karmic using the instructions above.

No campaigns, no options as yet, sound is a bit glitchy. But it looks really promising. Granted there's not much I could tell from the couple minutes i spent zooming in and out, rotating the camera and ordering units around.

---

