---
title: "Help with running perl scripts"
date: 2009-03-13
forum: General Help
---

### Post by darkfeline on 2009-03-13
I have a strange problems with running .pl files on my ubuntu.  I am able to run them via the terminal, but I cannot seem to be able to run them by double-clicking them.  I have the #!/usr/bin/perl as the first line, and the allow to run as an executable checked in the file properties.  When I double-click on the file, it asks to either run, run from terminal, display, or cancel.  Run doesn't do anything, run from terminal flashes something on the bar at the bottom of the screen for a moment then disappears.  The code runs normally from terminal i.e. no compilation errors.  Any ideas?

---

### Post by ad_267 on 2009-03-13
What is the script supposed to do? If it doesn't take any input and just prints to stdout, and you select run in terminal, it will run and then close the terminal as soon as it is finished.

You could try adding some statment at the end of the script to read in input from the user (I've never used perl before so don't know how to do this) so the terminal won't close.

---

### Post by darkfeline on 2009-03-13
Yes, my program asks for input.  It asks for input then searches the periodic table of elements for that element (I program for fun).  I have already tested it and it works fine through terminal.

---

### Post by ad_267 on 2009-03-14
Do you mind posting your script here? I tried with a very basic example:
```
#!/usr/bin/perl
print "Give me something:\n";
$var = <>;
print "You gave me: $var\n";
$var = <>;
```

If I double click on this and select run in terminal, a terminal pops up and the application runs as you'd expect. I included the extra "$var = <>;" at the end so the script doesn't quit until I press enter again. I haven't used Perl before and just got this off a random tutorial so I don't know if I'm doing everything right, but I don't have any problems running this from the file browser.

ALso, don't know if this is useful but you can change the default behaviour when opening an executable text file under Edit - Preferences - Behaviour - Executable Text Files.

---

### Post by darkfeline on 2009-03-14
Here's the code. 
```
#!/usr/bin/perl
# elementtable.pl
use warnings;
use strict;

#######################################
# Perl Table of Elements
# Made by darkfeline
# Dedicated to my raison d'entre =)
#  
# Version History:
#   1.0 03Mar2009
# It works!
#
#######################################

# turn off print buffer
$|=1;

# table, format sign,name,atom#,weight
my @table=(
	['H','Hydrogen',1, 1.00794],
	['He','Helium',2,4.00260],
	['Li','Lithium',3,6.941],
	['Be','Beryllium',4,9.01218],
	['B','Boron',5,10.811],
	['C','Carbon',6,12.011],
	['N','Nitrogen',7,14.0067],
	['O','Oxygen',8,15.9994],
	['F','Fluorine',9,18.9984],
	['Ne','Neon',10,20.1797],
	['Na','Sodium',11,22.9898],
	['Mg','Magnesium',12,24.3050],
	['Al','Aluminum',13,26.9815],
	['Si','Silicon',14,28.0855],
	['P','Phosphorus',15,30.9738],
	['S','Sulfur',16,32.066],
	['Cl','Chlorine',17,35.4527],
	['Ar','Argon',18,39.948],
	['K','Potassium',19,39.0983],
	['Ca','Calcium',20,40.078],
	['Sc','Scandium',21,44.9559],
	['Ti','Titanium',22,47.88],
	['V','Vanadium',23,50.9415],
	['Cr','Chromium',24,51.9961],
	['Mn','Manganese',25,54.9381],
	['Fe','Iron',26,55.847],
	['Co','Cobalt',27,58.9332],
	['Ni','Nickel',28,58.693],
	['Cu','Copper',29,63.546],
	['Zn','Zinc',30,65.39],
	['Ga','Gallium',31,69.723],
	['Ge','Germanium',32,72.61],
	['As','Arsenic',33,74.9216],
	['Se','Selenium',34,78.96],
	['Br','Bromine',35,79.904],
	['Kr','Krypton',36,83.80],
	['Rb','Rubidium',37,85.4678],
	['Sr','Strontium',38,87.62],
	['Y','Yttrium',39,88.9059],
	['Zr','Zirconium',40,91.224],
	['Nb','Niobium',41,92.9064],
	['Mo','Molybdenum',42,95.94],
	['Tc','Technetium',43,98],
	['Ru','Ruthenium',44,101.07],
	['Rh','Rhodium',45,102.906],
	['Pd','Palladium',46,106.42],
	['Ag','Silver',47,107.868],
	['Cd','Cadmium',48,112.411],
	['In','Indium',49,114.818],
	['Sn','Tin',50,118.710],
	['Sb','Antimony',51,121.76],
	['Te','Tellurium',52,127.60],
	['I','Iodine',53,126.904],
	['Xe','Xenon',54,131.29],
	['Cs','Cesium',55,132.905],
	['Ba','Barium',56,137.327],
	['La','Lanthanum',57,138.906],
	['Ce','Cerium',58,140.115],
	['Pr','Praseodymium',59,140.908],
	['Nd','Neodymium',60,144.24],
	['Pm','Promethium',61,145],
	['Sm','Samarium',62,150.36],
	['Eu','Europium',63,151.965],
	['Gd','Gadolinium',64,157.25],
	['Tb','Terbium',65,158.925],
	['Dy','Dysprosium',66,162.50],
	['Ho','Holmium',67,164.930],
	['Er','Erbium',68,167.26],
	['Tm','Thulium',69,168.934],
	['Yb','Ytterbium',70,173.04],
	['Lu','Lutertium',71,174.967],
	['Hf','Hafnium',72,178.49],
	['Ta','Tantalum',73,180.948],
	['W','Tungsten',74,183.84],
	['Re','Rhenium',75,186.207],
	['Os','Osmium',76,190.23],
	['Ir','Iridium',77,192.22],
	['Pt','Platinum',78,195.08],
	['Au','Gold',79,196.967],
	['Hg','Mercury',80,200.59],
	['Tl','Thallium',81,204.383],
	['Pb','Lead',82,207.2],
	['Bi','Bismuth',83,208.980],
	['Po','Polonium',84,209],
	['At','Astatine',85,210],
	['Rn','Rhenium',86,222],
	['Fr','Francium',87,223],
	['Ra','Radium',88,226.025],
	['Ac','Actinium',89,227.028],
	['Th','Thorium',90,232.038],
	['Pa','Protactinium',91,231.036],
	['U','Uranium',92,238.029],
	['Np','Neptunium',93,237.048],
	['Pu','Plutonium',94,244],
	['Am','Americium',95,243],
	['Cm','Curium',96,247],
	['Bk','Berkelium',97,247],
	['Cf','Californium',98,251],
	['Es','Einsteinium',99,252],
	['Fm','Fermium',100,257],
	['Md','Mendelevium',101,258],
	['No','Nobelium',102,259],
	['Lr','Lawrencium',103,260],
	['Rf','Rutherfordium',104,261],
	['Db','Dubnium',105,262],
	['Sg','Seaborgium',106,263],
	['Bh','Bohrium',107,262],
	['Hs','Hassium',108,265],
	['Mt','Meitnerium',109,266],
	['Ds','Darmstadtium',110,281]
);

print "Periodic Table of Elements, Perl edition.\nCoded by darkfeline.\nType 'quit' without quotes to quit.\n";

MAIN: while (1) {
	print "\nType the symbol, atomic number, name or part of the name of an element to search for: ";
	my $search=<STDIN>;
	chomp $search;
	my @result;

	# quit check
	if ($search =~ /^quit$/i) {
		print "\nExiting..." and sleep 2;
		last MAIN;
	}

	# entry-error checking
	if (not $search) {
		print "\nSee, in order to search for something, you need to type something. Smartass.\n";
		next MAIN;
	}
	
	if ($search =~ /[\W]/) {
		print "\nDude, either numbers or letters.  If you think there's an element with symbols in it, you need to lay off the mushrooms.\n";
		next MAIN;
	}

	if (($search =~ /\d/) and ($search =~ /[a-zA-Z]/)) {
		print "\nEither numbers or letters to search by atomic number or element name or symbol, respectively.  Not both.\n";
		next MAIN;
	}

	# atomic# searches
	if ($search =~/\d+/) {
		for (0..$#table-1) {
			if ($search==$table[$_]->[2]) {
				push @result,$table[$_];
			}
		}
	} else {
		# symbol searches, if symbol matches, add elementref to array, end
		for (0..$#table-1) {
			if (lc($search) eq lc($table[$_]->[0])) {
				push @result,$table[$_];
			}
		}

		# name searches, if still no match, look at names, and add matching elmntrefs to array
		if (not @result) {
			for (0..$#table-1) {
				if ($table[$_]->[1] =~ /$search/i) {
					push @result,$table[$_];
				}
			}
		}
		# multiple matches for name
		if ($#result > 0) {
			print "\n\nMultiple matches.  Please be more specific.\n";
		}
	}


	# print
	if (@result) {
		for (@result) {
			print "\nSymbol: ",$_->[0];
			print "\nElement: ",$_->[1];
			print "\nAtomic Number: ",$_->[2];
			print "\nAtomic Mass: ",$_->[3];
			print "\n";
		}
	} else {
		print "\nNo matches.  Please try again.\n";
	}
}
```

Changing the preferred method of opening executables yields the same effect as before (no response when run, no problem viewing the code).
I tried googling for my problem, but it seems rather unique, or maybe there's something ridiculously simple I'm missing.

---

### Post by ad_267 on 2009-03-14
Well that works for me, I select run in terminal and it runs properly. 

What do you have selected for your Terminal Emulator in System - Preferences - Preferred Applications - System?

I'm using gnome-terminal and the execute flag is set to -x.

Is this only a problem with Perl scripts, have you tried anything else scripts like Bash or Python scripts? Also you are using Gnome as your desktop environment right, ie. normal Ubuntu, not Xubuntu or Kubuntu?

---

### Post by darkfeline on 2009-03-14
not sure what BASH is, but my python programs also don't run.  They also work from terminal.  My system preferences are gnome-terminal and -x, no problem there.  I'm using regular Ubuntu, Intrepid Ibex.

Off-topic, but my python program acts strange on Ubuntu.  It runs without a hitch, but after asking for input a second time, it dies.  It worked fine on my windows xp.  I remember there being compatibility issues with 2.6 to 3.0.  What version does Intrepid Ibex have?

---

### Post by ad_267 on 2009-03-14
Well that's weird, I'm pretty stumped. The other thing you can do if you want to be able to run the script from the file browser or from the Desktop is to create a launcher for your script that runs "gnome-terminal -x /path/to/your/script.pl".

Intrepid has Python version 2.5.2, you can run "python --version" to find the Python version and the same thing works for many other applications. You can also use "apt-cache show python | grep Version".

Bash is the default shell, the thing that runs when you open a normal terminal window and enter commands into. You can use bash from the command line but can also write scripts for it (often called a shell script).

---

### Post by darkfeline on 2009-03-14
When I run the launcher, it says 'There was an error creating the child process for this window' and opens a blank terminal window.  Maybe it's just some weird quirk?  I'll just have to run them from the terminal.  It's not a real problem, it's just something to get used to.  Thanks for the help!

---

