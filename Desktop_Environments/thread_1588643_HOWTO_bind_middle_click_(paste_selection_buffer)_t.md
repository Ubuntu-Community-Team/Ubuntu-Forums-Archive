---
title: "HOWTO bind middle click (paste selection buffer) to keystroke"
date: 2010-10-05
forum: Desktop Environments
---

### Post by ectospasm on 2010-10-05
I have been looking for a way to make whatever window that has focus react as if I middle-clicked into it (paste selection buffer), using only the keyboard.

[SIZE="4"]Prerequisites[/SIZE]

I installed xmacro, xbindkeys, ruby, and xclip to get this working. For Debian/Ubuntu, you should be able to do this:

```
# aptitude -y install xmacro xbindkeys ruby xclip
```

[SIZE="4"]Set up Ruby script[/SIZE]

I downloaded this script from here: [http://whynotwiki.com/GNU/Linux_/_Desktop_/_Keyboard_shortcuts](http://whynotwiki.com/GNU/Linux_/_Desktop_/_Keyboard_shortcuts) ([COLOR="Red"]watch out, Chrome reports that this site may have malware[/COLOR], hence the rewriting and posting here).

The script essentially pipes an xmacro to standard out. This is used in the pasteBuf.sh script below to provide input to xmacroplay.

getBuf.ruby:
```
#!/usr/bin/env ruby

max_per_line = 10

contents = `xclip -o`
contents.each_line do |line|
        line.chomp!
        while (chunk = line.slice!(0..max_per_line)) != '' do
                puts "String #{chunk}"
        end
        #puts "KeyStrPress Return"
        #puts "KeyStrRelease Return"
end
```

(I tried recoding the script above in Perl, but my Perl is rusty enough to where I couldn't figure out how to do it. I'm close, just need to be able to tell Perl not to interpolate anything in the output).

EDIT:  Removed the press and release of Return at the end, since that isn't usually what I want (note the commented lines for KeyStrPress and KeyStrRelease).


[SIZE="4"]Set up execution script[/SIZE]

This is the script that X.org executes, which calls the getBuf.ruby script above. It calls getBuf.ruby to generate input for xmacroplay, which then types the buffer into the current window.


pasteBuf.sh:
```
#!/bin/sh

GETBUF=~/src/xmodstuff/getBuf.ruby
XMACRO_OPTS='-d 0'
SLEEP_DELAY='0.2'
sleep ${SLEEP_DELAY}
${GETBUF} | xmacroplay ${XMACRO_OPTS} ${DISPLAY}

```

[SIZE="4"]xbindkeys setup[/SIZE]

I tried setting the above script to a GNOME keybinding in Ubuntu, but that doesn't seem to work. I used the program xbindkeys to assign CTRL + ALT + V to the Paste Selection Buffer action:

~/.xbindkeysrc
```

"~/src/xmodstuff/pasteBuf.sh"
        control+alt + v

```

Then I had to start xbindkeys (with no options). I placed this into my startup scripts, and I'm done!

[SIZE="4"]Thoughts[/SIZE]

This is a hack. It seems to work very well, except it doesn't handle pasting code too well. I wrote a Perl script to replace the Ruby script, and it mostly works, though when I tried to paste it using this method it caused the Perl script to enter an infinite loop, and I had to kill my X session with CTRL-ALT-BACKSPACE (you may want to enable that key chord, just in case).

Here's my Perl script, to give you an idea.  I've fixed some logic in it, hopefully it works now.  Note that you [COLOR="Red"]SHOULDN'T USE THIS[/COLOR] because it's not tested.  

```
#!/usr/bin/perl -w

use strict;

my $maxChunk = 5;  

my $contents = qx/xclip -o/;
my @contents = split /\n/, $contents;
foreach my $item (@contents) {
	chomp $item;
	while ($item ne "") {
		my $chunk = substr($item, 0, $maxChunk);
		print "String $chunk\n";
		$item =substr($item, $maxChunk);
	}
	#print "KeyStrPress Return\n";
	#print "KeyStrRelease Return\n";
}

```

---

### Post by ectospasm on 2010-10-17
I've tested my Perl script, and it works now.  It seems on my current computer pasting formatted text doesn't work right, even with the Ruby code above.  Oh, well.  I can always use clipboard (the venerable CTRL-C/CTRL-V and related methods) for code.

My primary purpose was so I could have one thing in the clipboard memory and another in the selection buffer, and use them both strictly with keystrokes.  That is accomplished now.

---

