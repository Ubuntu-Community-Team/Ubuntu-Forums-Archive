---
title: "Slightly confused about the components of Gnome..."
date: 2007-07-03
forum: Desktop Environments
---

### Post by geek_Man on 2007-07-03
Can some please explain to me the different parts of Gnome? I know that Gtk2 is the thing that draws the buttons and stuff and that Metacity is the window manager and Nautilus is the... what? I know that Nautilus is the file browser, but I was also pretty sure it did other things. Please say if I missed something...

---

### Post by christhemonkey on 2007-07-03
Nautilus manages the desktop as well.

(so like draws the background and icons)

---

### Post by geek_Man on 2007-07-03
So what does Metacity, Fluxbox, and IceWM do?

---

### Post by christhemonkey on 2007-07-03
Metacity is a window manager, so it draws the bar at the top of the window with the minimise, quit (etc) buttons. And allows you to actually move windows and put one behind the other.


Fluxbox and IceWM are alternative window managers. They are not part of Gnome.

---

### Post by geek_Man on 2007-07-03
Yes, I knew that Fluxbox and IceWM were alternatives, I was just talking about window managers in general.

SO! Gtk2 defines the buttons and Metacity draws them? And what is Nautilus' icon draw-ey functionality called?

---

### Post by christhemonkey on 2007-07-03
Gtk2 is a widget tool kit.
See here:
[http://en.wikipedia.org/wiki/Widget_toolkit](http://en.wikipedia.org/wiki/Widget_toolkit)

Nautilus is a File Manager, not sure if its desktop component has an official name, maybe a desktop manager?

---

### Post by geek_Man on 2007-07-03
So, Gtk2 is the widgets and Metacity draws them?

BTW, you were a big help, man. Thanks.

---

### Post by christhemonkey on 2007-07-03
No worries.

Hmm, i wouldnt say metacity draws them, metacity actually handles the windows (their borders their position everything) and Gtk draws the windows contents (but only if a program is using the GTK toolkit :)).

A GUI is actually written by saying i would like to place such and such a GTK widget here. Now gtk please show this widget.

---

### Post by geek_Man on 2007-07-03
I have had a little experience with Gtk2-Perl, so kinda know how that stuff works (not that I would have remembered that).

---

### Post by christhemonkey on 2007-07-03
Cool.
Only had experience with PyGTK myself.

My C/C++ isnt goin very well atm...

---

### Post by geek_Man on 2007-07-03
I was gonna try to learn Python, but it's so different from Perl. So I'm just going to stick with Perl.

---

### Post by christhemonkey on 2007-07-03
Fair enough.

Whats Perl like? Never been tempted to learn it.

All examples of it i have ever seen just look fairly confusing.

---

### Post by geek_Man on 2007-07-03
It's pretty straight forward, I guess. You can do stuff as simple as: ```
print "Hello World!\n";
``` to ```
uh... stuff too complicated for me to understand...
```
Basically, you run functions and user-defined subroutines that returns stuff (kinda like most languages ;)). There's a lot of shortcuts in Perl to save heavy Perl programmers a bit of time. So, normally arguments are passed in parens, but you don't always have to do that in Perl. So it can look kinda strange... but I like it. It's good for data parsing, text parsing, CGI, gluing things together and lot of other stuff. Here's a slightly useless Gtk2-Perl script I wrote: ```
#!/usr/bin/perl

use warnings;
use Glib qw/TRUE FALSE/;
use Gtk2 '-init';
use Gtk2::Gdk::Keysyms;

sub convert {
    my ($widget, $data) = @_;
    my $text = $data->get_text();
    if ($text =~ /([0-9]+)/) {
        $text *= 1.024;
        $entry->set_text ("That equals $text");
    }
    else {
        $entry->set_text ("You idiot, that's not a number...");
    }
}

sub key_press_handler {
    my ($widget, $event) = @_;
    if ($event->keyval == $Gtk2::Gdk::Keysyms{Return} || $event->keyval == $Gtk2::Gdk::Keysyms{KP_Enter}) {
        convert($widget, $entry);
    }
    elsif ($event->keyval == $Gtk2::Gdk::Keysyms{Escape}) {
        delete_event();
    }
}

sub delete_event {
    Gtk2->main_quit;
    return TRUE;
}

$window = Gtk2::Window->new('toplevel');
$window->signal_connect(key_press_event => \&key_press_handler);
$window->signal_connect(delete_event => \&delete_event);
$window->set_title("Type in a number of megabytes to convert");
$window->set_border_width(20);
$window->set_default_icon_from_file("/usr/share/pixmaps/ubuntu.svg");

$box1 = Gtk2::HBox->new(FALSE, 0);
$window->add($box1);

$entry = Gtk2::Entry->new;
$button = Gtk2::Button->new("Convert");
$button->signal_connect(clicked => \&convert, $entry);

$box1->pack_start($entry, TRUE, TRUE, 0);
$box1->pack_start($button, TRUE, TRUE, 0);

$entry->show;
$button->show;
$box1->show;
$window->show;

Gtk2->main;

0;
```

Like I said, it's kinda useless, but I'm fond of it nonetheless.

---

### Post by geek_Man on 2007-07-03
I forgot to mention, you type in a number of megabytes and it spits it back out in binary ("correct") form. I wrote it for using Gparted.

---

### Post by christhemonkey on 2007-07-04
Just a couple of questions about that example!

Do all variables in perl have to begin with a "$"?

And what does @_ mean?

And Perl is an interpreted language isnt it?

---

### Post by geek_Man on 2007-07-04
All scalars begin with $. So you could have $foo = "geek_Man was here", $bar = 1024, and $sumthin = shift(). @_ is the arguments array. It's lexically scoped, so it changes for every subroutine. (Arrays start with @ and hashes start with %.) And yes, Perl is interpreted. No compiling, no nothing, perl does it for you.

---

### Post by christhemonkey on 2007-07-04
That sounds like a little bit of a headache!

But at least its nice and simple and interpreted. :D


Btw, tried your little program, works very well! But i dont think its a good idea to place the output into the same textbox as the input. But thats just my opinion!


One last quick Perl question, can you have classes in Perl?
To place your subroutines in.

---

### Post by geek_Man on 2007-07-04
Yeah, placing the output in the input box is kinda dumb, but my knowledge of Gtk2-Perl is kind of limited. It's the best I could come up with. Uh, you might have to explain what classes are, I think there are classes in OO Perl, but I'm not sure.

---

### Post by christhemonkey on 2007-07-04
So in Python,
I guess the equivalent of a subroutine is a function which you create by using "def function(arguments)"

So a little example of what a class is:
```
#!/usr/bin/env python

class Square:
	def __init__(self, (x, y)):
		self.x = x
		self.y = y
		print "Creating square of size",x,"by",y

	def area(self):
		return self.x*self.y

	def circ(self):
		return ((2*self.x)+(2*self.y))

class Circle:
	def __init__(self, radius):
		print "Creating circle of radius",radius
		self.radius = radius

	def area(self):
		return 3.14*self.radius*self.radius

	def circ(self):
		return 2*3.14*self.radius

while True:
	try:

		shape = raw_input("Select a shape (Square or Circle): ")

		if shape == "Square":
			xsize = input("Select X size: ")
			ysize = input("Select Y size: ")
			Square= Square((xsize,ysize))
			area = Square.area()
			circ = Square.circ()

		elif shape == "Circle":
			radius = input("Select Radius: ")
			Circle = Circle(radius)
			area = Circle.area()
			circ = Circle.circ()

		else:
			print "Please type either Square or Circle!"
			area = "\r        "
			circ = "\r                 "


		print "Area of:",area
		print "Circumference of:",circ
		print "Type Ctrl+C to break"

	except KeyboardInterrupt:
		print "\nGoodbye!"
		break
```


That was an awful example come to think of it, but never mind!
The thing to note, you could of initialised mutliple versions of each class with different sizes.

According to the great gods of wikipedia:
> In object-oriented programming, a class is a programming language construct that is used to group related instance variables and methods. A method, called a function in some languages, is a set of instructions that are specific to a class. Depending on the language, classes may support multiple inheritance or may require the use of interfaces to extend other classes. A class may indicate either specifically or abstractly what methods exist when the program is executed. The latter is known as an 'abstract class'.

---

### Post by geek_Man on 2007-07-04
Then, in short, yes, Perl has classes (I think).

---

### Post by christhemonkey on 2007-07-05
Cool. :D

Might have to give Perl a try, any good tutorials come to mind?

---

### Post by geek_Man on 2007-07-05
I actually borrowed "Programming Perl" from the library. It teaches all the basics, but it's a big book, so it teaches ALL the basics. I dunno if you have it at your library, but if not, (sorry to sound like everyone else) there's also Google. Just search for 'perl tutorial' and you'll get a bunch of results. Have fun!

---

### Post by christhemonkey on 2007-07-05
Cool, cheers! Been nice to chat.

---

### Post by geek_Man on 2007-07-05
Yeah, it was. Good luck.

---

