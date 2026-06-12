---
title: "Creating a custom keyboard layout"
date: 2010-01-22
forum: Desktop Environments
---

### Post by Freiberg on 2010-01-22
There have been some posts on this forum about custom keyboard layouts, but the latest one was more than three years ago, and is outdated.  I found the following code for a custom dvorak international keyboard layout [here]("http://arjenvankol.com/dvorak.php"), but it directs me to copy this code into the folder /etc/X11/xkb/symbols/pc, a folder which does not seem to exist in 9.10 or 9.04.
```

partial default alphanumeric_keys
xkb_symbols "basic" {
    name[Group1]= "Dvorak international extended";

    // Alphanumeric section

    key <TLDE> { [       dead_grave, dead_tilde	]	};

    key <AE01> { [	    1,	exclam, exclamdown, U00B9 ] };
    key <AE02> { [	    2,	at, U00B2 ]		};
    key <AE03> { [	    3,	numbersign, U00B3 ]	};
    key <AE04> { [	    4,	dollar, currency, U00A3	] };
    key <AE05> { [	    5,	percent, EuroSign ]	};
    key <AE06> { [	    6,	dead_circumflex, U00BC ]};
    key <AE07> { [	    7,	ampersand, U00BD ]	};
    key <AE08> { [	    8,	asterisk, U00BE	]	};
    key <AE09> { [	    9,	parenleft, U2018 ]	};
    key <AE10> { [	    0,	parenright, U2019 ]	};
    key <AE11> { [ bracketleft,	braceleft, guillemotleft ] };
    key <AE12> { [ bracketright, braceright, guillemotright ] };

    key <AD01> { [  dead_acute, dead_diaeresis, U00E4, U00C4 ] };
    key <AD02> { [	comma,	less, U00E5, U00C5 ]	};
    key <AD03> { [      period,	greater, U00F6, U00D6 ] };
    key <AD04> { [	    p,	P, paragraph, degree ]	};
    key <AD05> { [	    y,	Y, U00FC, U00DC	]	};
    key <AD06> { [	    f,	F		]	};
    key <AD07> { [	    g,	G, U00E7, U00C7	]	};
    key <AD08> { [	    c,	C, copyright, U00A2 ]	};
    key <AD09> { [	    r,	R, registered	]	};
    key <AD10> { [	    l,	L		]	};
    key <AD11> { [	slash,	question, questiondown ]};
    key <AD12> { [	equal,	plus, U00D7, U00F7 ]	};

    key <AC01> { [	    a,	A, U00E1, U00C1	]	};
    key <AC02> { [	    o,	O, U00E5, U00C5	]	};
    key <AC03> { [	    e,	E, U00E9, U00E9	]	};
    key <AC04> { [	    u,	U, U00FA, U00DA	]	};
    key <AC05> { [	    i,	I, U00ED, U00CD	]	};
    key <AC06> { [	    d,	D, U00F0, U00D0	]	};
    key <AC07> { [	    h,	H 		]	};
    key <AC08> { [	    t,	T, U00FE, U00DE	]	};
    key <AC09> { [	    n,	N, U00F1, U00D1	]	};
    key <AC10> { [	    s,	S, ssharp, section ]	};
    key <AC11> { [	minus,	underscore, yen	]	};
    key <BKSL> { [  backslash, bar, U00F8, brokenbar ]	};

    key <AB01> { [   semicolon,	colon,ae, AE ] };
    key <AB02> { [	    q,	Q, U00F8, U00D8	]	};
    key <AB03> { [	    j,	J 		]	};
    key <AB04> { [	    k,	K		]	};
    key <AB05> { [	    x,	X		]	};
    key <AB06> { [	    b,	B		]	};
    key <AB07> { [	    m,	M, U00B5	]	};
    key <AB08> { [	    w,	W		]	};
    key <AB09> { [	    v,	V		]	};
    key <AB10> { [	    z,	Z		]	};

    include "level3(ralt_switch)"
};
```

As this is the only thing I felt Windows did better than Ubuntu (custom keyboard layouts), I would love to be able to change the layout and finally seal the deal with Ubuntu.  Any help would be appreciated, and thank you for your time in reading this post.

UPDATE:

Roberto.tomas has written an excellent entry in ubuntu wiki about this, and includes the general information of creating a custom keyboard layout, which can be found [here]("https://help.ubuntu.com/community/Howto%3A%20Custom%20keyboard%20layout%20definitions").  For this specific keyboard layout information, however, continue reading.

---

### Post by Freiberg on 2010-01-22
Bump.

Anybody?

---

### Post by zankapfel on 2010-01-28
NOTE: this post has been edited. i got my keyboard layout working with the help given in this thread

i've been trying to do the same thing. here's what i have so far.

the directory that keyboard layouts are stored in for 9.10 is in **/usr/share/X11/xkb/symbols/**

there is an additional file you have to edit, **/usr/share/X11/xkb/rules/evdev.xml**, in order to get the keyboard preferences (System->Preferences->Keyboard) to recognize your new layout. [this site]("http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11") gives some good advice for editing the different files. (it's a tutorial for 8.10, but the files are identical, just in different directories)

now for the problems i was having. i got Ubuntu to *see* the keyboard layout i made, but it wasn't really *recognizing* it. every time i booted up or attempted to add my new layout, i got an error:

> Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10604000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

ALWAYS make sure you've written your code correctly. i started my layout from scratch, and of course the problem boiled down to a few missing commas.

my IPA keyboard layout for Ubuntu 9.10:
```
//IPA Characters
// a custom keyboard layout by an OSU linguistics undergrad student
// designed to use almost all of the symbols in the International Phonetic Alphabet

default
partial alphanumeric_keys modifier_keys 
xkb_symbols "basic" {

    name[Group1]= "IPA Characters";

    key.type[Group1]="FOUR_LEVEL";

    key <TLDE> {[     	U0303,	U0334			]};
    key <AE01> {[     	U0298,	U02B7,	U02E9,	U033C	]};
    key <AE02> {[	U01C0,	U032A,	U02E8		]};
    key <AE03> {[	U01C2,	U033A,	U02E7		]};
    key <AE04> {[	U01C3,	U02B2,	U02E6,	U033B	]};
    key <AE05> {[	U01C1,	U029F,	U02E5,	U027A	]};
    key <AE06> {[	U02B0,	U02B1,	U02DE,	U02B4	]};
    key <AE07> {[	U02E0,	U02E4,	U207F,	U02E1	]};
    key <AE08> {[	U0324,	U0330,	U032C		]};
    key <AE09> {[	U0361,	U035C,	U203F		]};
    key <AE10> {[	U0325,	U030A,	U007C,	U2016	]};
    key <AE11> {[	U0320,	U031E,	U0319,	U0308	]};
    key <AE12> {[	U031F,	U031D,	U0318,	U033D	]};

    key <AD01> {[	U0259, 	U028C,	U0250,	U025E	]};
    key <AD02> {[	  w,	U028D,	U0270,	U0265	]};
    key <AD03> {[	U025B,	  e,	U025C,	U0258	]};
    key <AD04> {[	U0279,	  r,	U027E,	U0280	]};
    key <AD05> {[	  t,	U03B8,	U0288		]};
    key <AD06> {[	  y,	U028F			]};
    key <AD07> {[	  u,	U028A,	U0289,	U0339	]};
    key <AD08> {[	U026A,	  i,	U0268,	U031C	]};
    key <AD09> {[	  o,	U0254,	U0153,	U00F8	]};
    key <AD10> {[	  p,	U0239			]};
    key <AD11> {[ bracketleft,	slash,	U2193,	U2191	]};
    key <AD12> {[ bracketright,	slash,	U2198,	U2197	]};
    key <BKSL> {[ 	U027B,	U027D,	U02B5,	U02B6	]};

    key <AC01> {[	  a,	U00E6, 	U0251,	U0252	]};
    key <AC02> {[	  s,	U0283,	U0282,	U026C	]};
    key <AC03> {[	  d,	U00F0,	U0256,	U0257	]};
    key <AC04> {[	  f,	U0278			]};
    key <AC05> {[	  g,	U0262,	U0260,	U029B	]};
    key <AC06> {[	  h,	U0266,	U0127,	U029C	]};
    key <AC07> {[	  j,	U025F,	U029D,	U0284	]};
    key <AC08> {[	  k,	  q,	U0263,	U0281	]};
    key <AC09> {[	  l,	U026B,	U028E,	U026D	]};
    key <AC10> {[ 	U02D0,	U02D1,	U0306		]};
    key <AC11> {[ 	U031A, 	U02BC, 	U02C8,	U02CC	]};

    key <AB01> {[	  z,	U0292,	U0290,	U026E	]};
    key <AB02> {[	  x,	U03C7,	U0267		]};
    key <AB03> {[	U00E7,	  c,	U0255,	U0291	]};
    key <AB04> {[	  v,	U03B2,	U028B,	U2C71	]};
    key <AB05> {[	  b,	U0238,	U0299,	U0253	]};
    key <AB06> {[	  n,	U014B,	U0272,	U0273	]};
    key <AB07> {[	  m,	U0271,	U0274		]};
    key <AB08> {[	U0276,	U0275,	U0264,	U026F	]};
    key <AB09> {[     	U0329,	U032F,	U002E		]};
    key <AB10> {[     	U0294,	U02A1,	U0295,	U02A2	]};

    include "level3(ralt_switch)"
};

```

---

### Post by Freiberg on 2010-01-28
Ok, and thank you for your efforts here. I'm not likely to see errors, but I will say something if I see something.

---

### Post by kutya61 on 2010-02-02
Here is a good method, which worked with intreped and now I tested on karmic liveCD. Don't know about jaunty, because when I upgraded from intrepid, some files changed in /usr/share/X11/xkb/. Now I use jaunty and custom layout works, but don't know how. ;)

I think the best way is not modifying files under /usr/share/X11/xkb/symbols/. Instead make your layout somewhere in your home directory, and symlink it into /usr/share/X11/xkb/symbols/
For example if you make a layout in the file ~/my-layout, then
```
sudo ln -s ~/my-layout /usr/share/X11/xkb/symbols/my-own-layout
```
All you have to modify is /usr/share/X11/xkb/rules/evdev.xml
Put this somewhere in it, but under the <layoutList> tag:
```

    <layout>
      <configItem>
        <name>my-own-layout</name>
        <shortDescription>My</shortDescription>
        <description>Layout1</description>
        <languageList><iso639Id>eng</iso639Id></languageList>
      </configItem>
      <variantList>
        <variant>
          <configItem>
            <name>mylayout</name>
            <description>Layout2</description>
          </configItem>
        </variant>
      </variantList>
    </layout>

```

This evdev.xml code suppose that your ~/my-layout file starts like this:
```
xkb_symbols "mylayout" { 
```

The main things are:
 - the name in ~/my-layout file after xkb_symbols (in this example **mylayout**) should be the same as <layout><variantList><variant><configItem><name> tag in evdev.xml
 - <layout><configItem><name> should be the same as the filename in /usr/share/X11/xkb/symbols/ (in this example **my-own-layout**)
 - you can set the <layout><configItem><languageList><iso639Id> whatever language you want, for example if you set it to **eng**, your layout will be shown in System->Keyboard->Layouts->Add->_**By Language**_->English
Here (in keyboard propeties) you will see the layout named as **Layout1 Layout2**, which comes from the <descripton> tags.

---

### Post by frederickjh on 2010-02-03
In reality you can simplify things as you only have one keyboard layout so you do not need the variant section but can replace the whole section with <variant/> tag

I am using the same Dvorak International Extended keyboard with deadkeys from [http://arjenvankol.com/dvorak.php]("http://arjenvankol.com/dvorak.php") .  

[COLOR="Red"]**I have added an new post to this thread with new and better instructions and a new attachment. Please use them. Thanks!**[/COLOR]

Here is how I got it to work.

Save the attached text file as a file called DVX in the /usr/share/X11/xkb/symbols/ directory (I had to add the ".txt" to the end to be able to upload it). You will want to save it here instead of link to it if you want other user on the system to be able to use it.

 Then add the following lines to /usr/share/X11/xkb/rules/evdev.xml just before the </layoutList> tag.  

```
<layout>
      <configItem>
        <name>DVX</name>
        <shortDescription>DVX</shortDescription>
       <description>Dvorak International Extended (dead keys)</description>
        <languageList><iso639Id>eng</iso639Id></languageList>
     </configItem>
      <variantList/>
    </layout>
```

This worked for me on Karmic 9.10 the DVX show up as the layout indicator so I can differentiate it from the USA keyboard layout.

Frederick

---

### Post by Freiberg on 2010-02-03
Ok, I'm good until the part where you edit evdev.xml.  For some reason it will not let me edit that file, only read it.  Do I need to run a sudo command to edit it?

---

### Post by kutya61 on 2010-02-03
frederickjh: I think your method works, because you marked your layout as default, tricky... ;)

Freiberg: Yes, you should edit it with
```
sudo gedit /usr/share/X11/xkb/rules/evdev.xml
```
because this file is out of your home directory.

---

### Post by Freiberg on 2010-02-03
That almost seemed to work.  I saved the file sucessfully, but when I tried to select the layout, I got the following error:

```

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10604000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

```

---

### Post by kutya61 on 2010-02-03
Could you post, what you wrote in evdev.xml?

---

### Post by Freiberg on 2010-02-03
I posted exactly what frederickjh posted earlier.  Reposting, that is:

```
<layout>
      <configItem>
        <name>DVX</name>
        <shortDescription>DVX</shortDescription>
       <description>Dvorak International Extended (dead keys)</description>
        <languageList><iso639Id>eng</iso639Id></languageList>
     </configItem>
      <variantList/>
    </layout>
```

---

### Post by kutya61 on 2010-02-03
Ok, you should modify it a bit. From your first post I think, that the file which contains your layout is in the /usr/share/X11/xkb/symbols/pc/ directory. You should copy your layout file into /usr/share/X11/xkb/symbols/ (one directory upper). After this copy, paste the name of that file here:

```
<layout>
      <configItem>
        <name>**name of the file**</name>
        <shortDescription>DVX</shortDescription>
       <description>Dvorak International Extended (dead keys)</description>
        <languageList><iso639Id>eng</iso639Id></languageList>
     </configItem>
      <variantList/>
    </layout>
```

For example, if your layout file is /usr/share/X11/xkb/symbols/mydvorak then in your evdev.xml the above line should be this:
```
        <name>**mydvorak**</name>
```

---

### Post by Freiberg on 2010-02-03
It worked!  It worked!

I realized the basic problem: I had not actually saved DVX in the symbols directory.  I took the text from DVX and copied it.  Then, I opened a terminal and used a sudo gedit.  From there, I pasted the text, saved it as DVX in the symbols directory, and bang!  It worked like a charm.

Thank you all very much for your help: I could not have done this without you.  I am marking this thread as solved.

---

### Post by kutya61 on 2010-02-03
You are welcome.

---

### Post by frederickjh on 2010-02-04
> **kutya61 said:**
> 
Freiberg: Yes, you should edit it with
```
sudo gedit /usr/share/X11/xkb/rules/evdev.xml
```
because this file is out of your home directory.

You can also hit Alt-F2 to bring up the _Run Application_ dialog. Then type in gksu followed by the program you want to run as the super user. Many times in a project like this I will run the file manager with the run application dialog by typing in _gksu nautilus_. Then if I then need to edit a file I open it from the file manager and it opens gedit with super user privileges so I can edit it.

[COLOR="Red"]**:!: Warning: If you don't know what you are doing you can mess up your computer big time running programs as the super user! Always make a backup copy of files before you edit them so you always have something to go back to.  If you mess your computer up running as super user don't blame me [-X you have been warned.**[/COLOR]

---

### Post by frederickjh on 2010-02-07
I figured out that if the layout file is named in lowercase characters only and the layout is added to the evdev.lst then the indicators and group names show up.

So, add the following line to the end of the section _! layout_ in the /usr/share/X11/xkb/rules/evdev.lst file.

  dvx        Dvorak International Extended (dead keys)

This is just before the section _! variant_.

If you followed my previous instructions in my previous post then you will need to also change the 

<name>DVX</name>   to <name>dvx</name> in the code to be inserted in the evdev.xml file and rename the DVX file in the /usr/share/X11/xkb/symbols directory to dvx. Change both the filename and the reference to it to all lower case.

============================================================
If you are starting fresh follow the instructions below which I have edited to be complete and use the newly attached file with the complete instructions.

> **frederickjh said:**
> In reality you can simplify things as you only have one keyboard layout so you do not need the variant section but can replace the whole section with <variant/> tag

I am using the same Dvorak International Extended keyboard with deadkeys from [http://arjenvankol.com/dvorak.php]("http://arjenvankol.com/dvorak.php") .  

Here is how I got it to work.

Save the attached text file as a file called dvx in the /usr/share/X11/xkb/symbols/ directory (I had to add the ".txt" to the end to be able to upload it). You will want to save it here instead of link to it if you want other user on the system to be able to use it.

 Then add the following lines to /usr/share/X11/xkb/rules/evdev.xml just before the </layoutList> tag.  

```
<layout>
      <configItem>
        <name>dvx</name>
        <shortDescription>DVX</shortDescription>
       <description>Dvorak International Extended (dead keys)</description>
        <languageList><iso639Id>eng</iso639Id></languageList>
     </configItem>
      <variantList/>
    </layout>
```

Then, add the following line to the end of the section _! layout_ in the /usr/share/X11/xkb/rules/evdev.lst file.

  dvx		  Dvorak International Extended (dead keys)

This is just before the section _! variant_.

This worked for me on Karmic 9.10 the DVX show up as the layout indicator so I can differentiate it from the USA keyboard layout.

Frederick

I hope this helps someone else.

Frederick

---

### Post by lucius.antonius on 2010-02-09
Here's a blogpost that explains how I customized my own keyboard on karmic: [http://www.doink.ch/an-x11-keyboard-layout-for-scholars-of-old-germanic/](http://www.doink.ch/an-x11-keyboard-layout-for-scholars-of-old-germanic/)

---

### Post by deeflex on 2010-03-05
> **frederickjh said:**
> I figured out that if the layout file is named in lowercase characters only and the layout is added to the evdev.lst then the indicators and group names show up.

So, add the following line to the end of the section _! layout_ in the /usr/share/X11/xkb/rules/evdev.lst file.

  dvx        Dvorak International Extended (dead keys)

This is just before the section _! variant_.

If you followed my previous instructions in my previous post then you will need to also change the 

<name>DVX</name>   to <name>dvx</name> in the code to be inserted in the evdev.xml file and rename the DVX file in the /usr/share/X11/xkb/symbols directory to dvx. Change both the filename and the reference to it to all lower case.

============================================================
If you are starting fresh follow the instructions below which I have edited to be complete and use the newly attached file with the complete instructions.



I hope this helps someone else.

Frederick

That worked like a charm! ;)

---

### Post by roberto.tomas on 2010-05-20
hey guys - I wrote up, at elast the general ideas presented here, in the ubuntu wiki: [https://help.ubuntu.com/community/Howto%3A%20Custom%20keyboard%20layout%20definitions](https://help.ubuntu.com/community/Howto%3A%20Custom%20keyboard%20layout%20definitions) -- please have a look. I'd already done so much work on it before I found your thread, I decided no one should ahve to go through all that again :)

---

### Post by Freiberg on 2010-05-20
That is a really good, and concise, guide to doing this.  If you don't mind, I'm going to try to edit my first post and put that link there, so that everybody can see it.

---

### Post by errarel on 2010-09-20
This guide by Roberto is great, but it requires superuser permissions.
Is there a way to do it in userspace?
I guess I need to copy some of /usr/share/X11/xkb/ files into ~/xkb/ and run
```
setxkbmap -I~/xkb/ -something something mylayout myvariant
```but I can't get it working

---

### Post by frederickjh on 2010-09-20
See post #5. You can create a link but then your layout will only be available for the current user. You will still need to be root to make the link or links that you need.

Greetings

Frederick

---

### Post by ernsttremel on 2010-12-05
In Microsoft's keyboard layout creator there one may 
create keystrokes like
[COLOR=Red]U+014b U+02b8[/COLOR], i.e. [SIZE=4][COLOR=Red]&#331;&#696;[/COLOR][/SIZE] one keystroke delivers a composed glyph. 

Is such a proceeding possible in Ubuntu, too?
for example
key <TILDE> { [ UE107,    [COLOR=Red]U014B U02B8[/COLOR] ] }; // &#57607; [SIZE=4][COLOR=Red]&#331;&#696;[/COLOR][/SIZE]

---

### Post by ptoche on 2013-04-05
A big thank you to everyone who has contributed these tips, esp. the OP  :)

Below are the steps that work for me, for the record.

Note the importance of removing the .xkm files. To test that your layout is being read properly, do something silly like assigning the number 1 to the letter z. These .xkm files nearly drove me mad.

```

3-step instructions (see further down for details):

  sudo cp ~/workspace/dv.txt /usr/share/X11/xkb/symbols/dv # copy layout, remove .txt extension in the process
  sudo rm /var/lib/xkb/*.xkm # force recompile of the xkm files
  sudo rm /usr/share/X11/xkb/symbols/dv~ # clean up 


 Dvorak customized keyboard layout for Ubuntu
 version 0.01
ptoche

 Install instructions:

 replace -kate- by your editor, e.g. -gedit- 

 1.

 copy the layout file dv into /usr/share/X11/xkb/symbols

  $ sudo cp ~/mykeyboard/dv /usr/share/X11/xkb/symbols

 2.

 edit the evdev.xml file to include a reference to the new layout:

 $ sudo kate /usr/share/X11/xkb/rules/evdev.xml

 In the editor, insert the following reference to the layout:

  <layoutList>
    <layout>
    ...
    </layout>
    <layout>
      <configItem>
        <name>dv</name>
        <shortDescription>dv</shortDescription>
        <description>myDvorak</description>
        <languageList><iso639Id>eng</iso639Id></languageList>
      </configItem>
      <variantList>
        <variant>
          <configItem>
            <name>dv-variant</name>
            <description>myDvorakVariant</description>
          </configItem>
        </variant>
      </variantList>
    </layout>
  </layoutList>

 This may need to be done again after a major operating system upgrade.


 3.

  $ sudo kate /usr/share/X11/xkb/rules/evdev.lst

 In the editor, add the following line to the end of the layout section :

 !model
 ...
 
 !layout
 ...
  dv              Dvorak Layout (Custom)
 
 !variant
 ...

 This may need to be done again after a major operating system upgrade.


 4.

  $ sudo rm /var/lib/xkb/*.xkm
 
 According to 'man setkxbmap':
 "An XKB keymap is constructed from a number of components which are compiled only as needed. 
 The source for all of the components can be found in /usr/share/X11/xkb"

 The new layout will have no effect until the system recompiles.
 Removing the .xkm files forces a recompilation.

 and just in case, remove any backup of your custom layout:

  $ sudo rm /usr/share/X11/xkb/symbols/dv~


 2013/04/05 


```

---

### Post by oldos2er on 2013-04-05
Old thread closed.

---

