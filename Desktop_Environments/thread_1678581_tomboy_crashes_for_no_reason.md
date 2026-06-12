---
title: "tomboy crashes for no reason"
date: 2011-01-30
forum: Desktop Environments
---

### Post by tanyeun on 2011-01-30
my tomboy always ran very fluently until 
one day I tried the tomboy-image patch.

When I tried to resize a big image in my note,
tomboy crashed. This was the first time I experienced
tomboy crashed.

I felt bothered. As a result, I removed the tomboy-image.

Later on, sometimes I clicked on a link to another note 
or when I clicked on a note and then tomboy crashed. 
It is not very often but bothered me a lot. 
Especially after I kill the process, I can't reopen it right away. I have to wait a while. 

I don't know if it relates to the installation
of tomboy-image or not? Since I already remove
it, how can it still in effect?Or tomboy normally
acts not that fluent when the amount of notes 
become larger? (I have 6xx notes so far)


any ideas?

thx,

David

---

### Post by sharm on 2011-01-30
Tomboy can handle thousands of notes without crashing, so that's not the problem.

Probably tomboy-image did something that's confusing Tomboy.  If you can find a way to reliably reproduce the crashes, please do this:

1) Quit Tomboy (make sure it's not running in the task manager!)
2) Open a terminal
3) Start Tomboy in the terminal with the command `tomboy --debug`
4) Do the steps to reproduce the crash
5) Copy the output from the terminal (which should include information about the crash) and paste it here

With the specific crash output, we should be able to figure out what's up, and can probably manually fix your notes by editing tomboy-image stuff out of the .note files.  Feel free to bug me (sandy) in #tomboy on irc.gnome.org, or on tomboy-list, or in Tomboy on GNOME bugzilla as well.

---

### Post by tanyeun on 2011-02-01
thx for the reply sharm
I located one of the note that caused the crash
and I found out the reason is because 
after I uninstall tomboy-image
the image part in the note became 
extremely huge weird strings
which caused tomboy very long time to response
I need to keep this note because 
some informations are important to me

is there any way to edit it efficiently
(delete the 'weird' part) ?

txt files in the ~/.tomboy files are encrypted
I couldn't tell which one is mine buggy note Orz

---

### Post by sharm on 2011-02-01
tanyeun and I got his notes fixed on IRC. Found the problem note, removed the tomboy-image binary data from it, and all was well.

---

### Post by tanyeun on 2011-02-01
thx, for sandy's patience to help me out on irc.
here is the solution:
for example, the buggy note's name is ABC
> 
$ cd ~/.local/share/tomboy
$ grep "ABC" -R .
/x.note: ...
$ vi x.note

then delete the lengthy strings
x = encryption of your title

---

### Post by drcabbage on 2011-02-08
Right.. so I'm getting the same problem with one of my notes that uses tomboy-image.  I disabled the addon and delete all the weird code mess that the addon leaves behind.  Problem is, it still won't start up. I have tried to match up my note to a working not, making sure I still had all the tags right.. but it still doesn't work..

Any help would be appreciated, thank you. 

Here is the note:
```
<?xml version="1.0" encoding="utf-8"?>
<note version="0.3" xmlns:link="http://beatniksoftware.com/tomboy/link" xmlns:size="http://beatniksoftware.com/tomboy/size" xmlns="http://beatniksoftware.com/tomboy">
  <title>Chapter 11</title>
  <text xml:space="preserve"><note-content version="0.1">Chapter 11

<size:huge>Intermolecular Forces, Liquids, and Solids</size:huge>

<size:large>States of Matter</size:large>
<list><list-item dir="ltr">fundamental different between states is the distance between them
</list-item><list-item dir="ltr">Condensed phases
<list><list-item dir="ltr">Solid and liquid states
</list-item></list></list-item><list-item dir="ltr">states depend on temperature
</list-item><list-item dir="ltr">pressure depends on two antagonistic entities
<list><list-item dir="ltr">the kinetic energy of the particles
<list><list-item dir="ltr">gas has highest motion thusly most pressure
</list-item></list></list-item><list-item dir="ltr">the strength of the attractions between the particles</list-item></list></list-item></list>

<size:large>Intermolecular Forces</size:large>
<list><list-item dir="ltr">attractions between molecules are not nearly as strong as the intermolecular attractions that hold compounds together
</list-item><list-item dir="ltr">they become closer when they get colder
</list-item><list-item dir="ltr">intermolecular attractions are always weaker than ionic and covalent bonds</list-item></list>


<size:large>London Dispersion Forces</size:large>
<list><list-item dir="ltr">When helium atoms cool down, it  changes shape
<list><list-item dir="ltr">moves all of its protons to one side
</list-item><list-item dir="ltr">the protons are attracted to the electrons
</list-item><list-item dir="ltr">electrons do not revolve around the nuclceous
</list-item></list></list-item><list-item dir="ltr"><highlight>all atoms and molecules go through LDF</highlight>
</list-item><list-item dir="ltr">the weakest intermolecular attraction
</list-item><list-item dir="ltr">they are dipole - <link:internal>Chapter 6</link:internal>
</list-item><list-item dir="ltr">polarization
<list><list-item dir="ltr">tendency of an electron cloud to distort in this way [ppt]</list-item></list></list-item></list>

<size:large>Factors Affecting London Forces</size:large>
<list><list-item dir="ltr">shape of the molecule affects the strength of dispersion forces
<list><list-item dir="ltr">long, skinny molecules (like n-pentance then to have stronger dispersion forces than short, fat ones (like neopentance) - <link:internal>Chapter 2</link:internal>
</list-item><list-item dir="ltr">due to an increased surface are in n-pentane
</list-item><list-item dir="ltr">skinny chains have more surface area to give more force
</list-item></list></list-item><list-item dir="ltr">Increase with increased molecular weight
<list><list-item dir="ltr">the higher the molecular weight makes it harder to escape all the bonds (boiling point)
</list-item><list-item dir="ltr">larger atoms haver larger electron clouds which are easier to polarize</list-item></list></list-item></list>

<size:large>Dipole-Dipole Interations</size:large>
<list><list-item dir="ltr">molecules that have permanent dipoles are attracted to each other
<list><list-item dir="ltr">the postive end attracted to a negative end and vise versa
</list-item></list></list-item><list-item dir="ltr">the more polar the molecule, the higher is its boiling point
<list><list-item dir="ltr">the more polar, the more difficult they are to break, the higher boiling point
</list-item><list-item dir="ltr">electronegativity - <link:internal>Chapter 6</link:internal></list-item></list></list-item></list>

<size:large>Hydrogen Bonding</size:large>
<list><list-item dir="ltr">the dipole-dipole interactions experienced when H is bonded to N, O, or F are unusually strong
</list-item><list-item dir="ltr">H2O have a higher D-D attraction then HCl because of the Hydrogen Bonding
</list-item><list-item dir="ltr">H2O and NH3 are Hydrogen bonded because they both have a H and N, O, or F
</list-item><list-item dir="ltr">shape of snowflake depends on temperature
<list><list-item dir="ltr">the temperature depends how they bond
</list-item><list-item dir="ltr">geometry - <link:internal>Chapter 9</link:internal>
</list-item></list></list-item><list-item dir="ltr">a stronger D-D attraction</list-item></list>

<size:large>Ion-Dipole Interactions</size:large>
<list><list-item dir="ltr">NaCl dissociates in H20 very well because of the massive amount of O for Na and H for Cl fight for it
</list-item><list-item dir="ltr">strongest interaction
</list-item><list-item dir="ltr">ionic (<link:internal>Chapter 2</link:internal>)substance dissolving in polar substance</list-item></list>

<size:large>Difference between Diamond and Graphite?</size:large>
<list><list-item dir="ltr">Diamond is tetrahedral
<list><list-item dir="ltr">very strong bond
<list><list-item dir="ltr">covalent bond?
</list-item></list></list-item><list-item dir="ltr">overlapped so nicely it is strong
</list-item></list></list-item><list-item dir="ltr">Graphite
<list><list-item dir="ltr">covalent bonding very strong</list-item></list></list-item></list>

<size:large>Viscosity</size:large>
<list><list-item dir="ltr">resistance of a liquid to flow
</list-item><list-item dir="ltr">increases with stronger intermolecular forces
</list-item><list-item dir="ltr">decreases with higher temperature</list-item></list>


<size:large>Surface Tension</size:large>
<list><list-item dir="ltr">H2O has strong surface tension due to strong intermolecular forces</list-item></list>

<size:large>Phase Changes
</size:large>

<size:large>Vapor Pressure</size:large>
<list><list-item dir="ltr">at any temperature some molecules in a liquid have enough energy to escape
</list-item><list-item dir="ltr">as the temperature rises, the fraction of molecules that have that enough energy to escape increases
</list-item><list-item dir="ltr">at all points, liquid is trying to escape
</list-item><list-item dir="ltr">as more molecules try to escape, the more the pressure increases
</list-item><list-item dir="ltr">equilibrium
<list><list-item dir="ltr">point at which the escape and the pressure of atmospheric pressure is equal
</list-item></list></list-item><list-item dir="ltr">boiling point
<list><list-item dir="ltr">the temperature at which it's vapor pressure equals atmospheric pressure
</list-item><list-item dir="ltr">the less atmospheric pressure, the lower the boiling point
</list-item><list-item dir="ltr">point at which its at equilibrium
</list-item><list-item dir="ltr">normal boiling point = 760 torr
</list-item></list></list-item><list-item dir="ltr">vaporization
<list><list-item dir="ltr">past boiling point</list-item></list></list-item></list>

<size:large>Phase Diagrams</size:large>
<list><list-item dir="ltr">display the state of a substance at various pressures and temperatures and the places where equilibria exist between phases
</list-item><list-item dir="ltr">to get all three phases at once
<list><list-item dir="ltr">give it slightly about 0 C and drop the pressure to almost 0
<list><list-item dir="ltr">due to the strong van der Waals forces between water molecules
</list-item></list></list-item><list-item dir="ltr">triple point
</list-item></list></list-item><list-item dir="ltr">a lot of energy is used to phase change and not put into atmosphere as much</list-item></list>



<size:large>Heat of Fusion</size:large>
<list><list-item dir="ltr">energy required to melt a solid
</list-item><list-item dir="ltr">/\H sub f
</list-item><list-item dir="ltr">H20
<list><list-item dir="ltr"><highlight>6.01 KJ / mol = 6.01 KJ / 18 g</highlight></list-item></list></list-item></list>

<size:large>Heat of Vaporization</size:large>
<list><list-item dir="ltr">energy required to vaporize a liquid
</list-item><list-item dir="ltr">/\H sub {vap}
</list-item><list-item dir="ltr">H2O
<list><list-item dir="ltr">40.7 KJ / mol = 40.7 KJ / 18g</list-item></list></list-item></list>



<size:large>Phase Change Calculate</size:large>
<list><list-item dir="ltr">EX:
<list><list-item dir="ltr">[notebook]</list-item></list></list-item></list>


<size:large>Covalent-Network and Molecular Solids</size:large>
<list><list-item dir="ltr">graphite is an example of a molecular solid, ion which atoms are held together with van der Waals forces
<list><list-item dir="ltr">tend to be softer and have lower melting points</list-item></list></list-item></list>

<size:large>Solids</size:large>
<list><list-item dir="ltr">crystalline
<list><list-item dir="ltr">highly ordered arrangement
</list-item></list></list-item><list-item dir="ltr">amorphous
<list><list-item dir="ltr">no particular order in the arrangement of particles
</list-item></list></list-item><list-item dir="ltr">packing
<list><list-item dir="ltr">ions pack themselves so as to maximize the attractions and minimize repulsions between the ions
</list-item><list-item dir="ltr">must repeat / have pattern
<list><list-item dir="ltr">ABAB
<list><list-item dir="ltr">hexagonal close-packing (HCP)
</list-item></list></list-item><list-item dir="ltr">ACBA
<list><list-item dir="ltr">cubic close-packing (CCP)</list-item></list></list-item></list></list-item></list></list-item></list>

<size:large>Types of Bonding in Crystalline Solids</size:large>
<list><list-item dir="ltr">if you have covalent bonds, you always have covalent network
</list-item><list-item dir="ltr">if you have electrostatic attractions, you always have ionic network</list-item></list>


<size:large>Metallic Solids</size:large>
<list><list-item dir="ltr">metals are not covalently bonded
<list><list-item dir="ltr">but attractions between atoms are too strong to be van der Waals
</list-item></list></list-item><list-item dir="ltr">atoms share the electrons between all
<list><list-item dir="ltr">try to trow the electrons as far as possible</list-item></list></list-item></list>

<size:large>Crystalline Solids</size:large>
<list><list-item dir="ltr">perfect ruby
<list><list-item dir="ltr">Al2O3
</list-item></list></list-item><list-item dir="ltr">because of the ordered in a crystal, we can focus on the repeating pattern of arrangement (unit cell)</list-item></list>
</note-content></text>
  <last-change-date>2010-08-03T02:01:20.6526090-04:00</last-change-date>
  <last-metadata-change-date>2011-02-02T19:33:20.8650060-05:00</last-metadata-change-date>
  <create-date>2010-09-02T16:35:30.9566150-04:00</create-date>
  <cursor-position>42</cursor-position>
  <width>424</width>
  <height>589</height>
  <x>0</x>
  <y>0</y>
  <tags>
    <tag>system:notebook:CHEM 106</tag>
  </tags>
  <open-on-startup>False</open-on-startup>
</note>
```

---

### Post by tanyeun on 2011-02-10
I have no clue what ur problem is, try to find sandy on irc

---

### Post by sharm on 2011-02-17
@drcabbage are you sure that note is the problem? does removing it allow Tomboy to start up normally?

---

