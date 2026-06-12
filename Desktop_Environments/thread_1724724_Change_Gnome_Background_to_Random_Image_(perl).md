---
title: "Change Gnome Background to Random Image (perl)"
date: 2011-04-08
forum: Desktop Environments
---

### Post by rocuan on 2011-04-08
First, I wrote a bare bones bash script to change the gnome desktop background to a random image
- [http://ubuntuforums.org/showthread.php?p=10479253](http://ubuntuforums.org/showthread.php?p=10479253)

Then, I realized there are *dozens* of bash scripts posted in the ubuntu forums just like this one
- [http://ubuntuforums.org/showthread.php?t=329164](http://ubuntuforums.org/showthread.php?t=329164) 
    
Next, rothalem & I rediscovered the drama of processing files in bash that have spaces in the name 
- [http://ubuntuforums.org/showthread.php?p=10496459](http://ubuntuforums.org/showthread.php?p=10496459)

Finally, sflitman suggested dumping bash all together & just using perl 
- [http://ubuntuforums.org/showthread.php?p=10635809#post10635809](http://ubuntuforums.org/showthread.php?p=10635809#post10635809) 
[B]
Result : [/B]
A pretty little perl script to change the gnome desktop wallpaper / background to a random image.
- If you are unfamiliar with perl : [http://www.comp.leeds.ac.uk/Perl/start.html](http://www.comp.leeds.ac.uk/Perl/start.html) 

The completed script isn't bullet proof but it will : 
- accept command line arguments
- accept files & dirs with spaces in the name
- catch most errors or use the defaults. 

**Step 1 : **Inherit the appropriate CPAN library ( from command line )
- Main Menu -> Accessories -> Terminal```
sudo cpan File::Random
```**Step 2 : **Cut-n-Paste this code into a perl script & change [COLOR=DarkRed]red line[/COLOR] to the path_to_your_wallpaper_images
```

#!/usr/bin/perl -w
# rocuan & sflitman
use Cwd;
use strict;
use File::Random qw/random_file/;
use Getopt::Long; Getopt::Long::Configure( "bundling" );

# HELP
sub usage 
{
    print "USAGE : $0\n";
    print " -d --dir <path>       valid dir w jpg|jpeg|png images\n";
    print " -h --help             print this usage statement\n";
    print " -i --image <path>     image path : dir/image or local\n";
    print " -r --recursive        search folders recursively\n";
    print " -v --verbose          print selected image to stdout\n";
    exit 0;
}

# DECLARE
my $depth   = 0;                  # default is non recursive search
my $image   = 0;                  # default is random image
my $verbose = 0;                  # default is quiet
my $cwd     = cwd();              # current working dir
my $dir     = "$ENV{HOME}/[COLOR=DarkRed]Pictures/Wallpaper[/COLOR]";                   
my $gconf   = "gconftool-2 -t str -s /desktop/gnome/background";
my $type    = ( qr/\.(?:jpg|jpeg|png)$/i );                 

# FLAGS
GetOptions( 'd|dir=s'     => \$dir,
            'h|help'      => \&usage,
            'i|image=s'   => \$image,
            'r|recursive' => \$depth,
            'v|verbose'   => \$verbose ) or die &usage;

# MAIN
# if local path & dir are valid : reassign
if( -d "$cwd/$dir" ) { $dir = "$cwd/$dir"; }

# if local path & image are valid : set
if( -e "$cwd/$image" ) { &setPic( $verbose, "$cwd/$image" ); }

# if full path & image are valid : set
elsif( -e $image ) { &setPic( $verbose, $image ); }

# if directory is valid
elsif( -d $dir )  
{
    # if random image definition is successful : set
    if( $image = random_file( -dir=>$dir, -recursive=>$depth, -check=>$type ) )
    {
        $dir =~ s/\/*$//; # cut trailing slash
        &setPic( $verbose, "$dir/$image" );
    }
    else{ &usage; }
}
else{ &usage; }


# SET 
# input : ( verbose true|false, image_path )
sub setPic
{
    my $verbose = shift;
    my $image = shift;
    if( $verbose ) { print "Selected $image\n"; }
    system qq{ $gconf/picture_filename "$image" };
    system qq{ $gconf/picture_options zoom };  
}

```[COLOR=DarkRed]Remember:[/COLOR]
- make it executable via command line -> chmod a+x yourscript.pl
- put your scripts in the right place: $HOME/bin -> [http://ubuntuforums.org/showthread.php?t=368125](http://ubuntuforums.org/showthread.php?t=368125)

**Default settings :**
- search the /home/user/Pictures/Wallpaper directory & ignore the sub directories
- choose a random jpg|jpeg|png image
- set that image as gnome desktop background using gconftool-2

**Options :**
-d   user defined directory with or without trailing slash
-h   usage statement with appropriate flags
-i set user defined image via full path or local path
-r   search folders recursively
-v   print path of selected image to stdout
* empty dirs or invalid data will result in usage statement or default settings

The command line flags can be either short( -h ) or extended( --help ) or bundled together( -vrd <directory> )

**Note :**
The perl command [COLOR=DarkGreen]GetOptions[/COLOR] uses key=>value pairs( hashes ) to define each flag.
It can be tricky to wrap your brain around how GetOptions works.
These are decent tutorials :
- [http://www.perlhowto.com/parsing_command_line_parameters_with_getopt_long](http://www.perlhowto.com/parsing_command_line_parameters_with_getopt_long) 
- [http://www.vromans.org/johan/articles/getopt.html](http://www.vromans.org/johan/articles/getopt.html)

*Thanx to both rothalem & sflitman for keeping me interested in this*

---

### Post by N33k on 2011-04-09
I was looking for something similar to this when I found it, I wondered how I might change it to only change the wallpaper when ever the screen goes off, such as when I shut down, reboot, or suspend, and maybe whenever the screensaver starts. Would it be possible to do that? If you could tell me how, I'd modify it myself, not asking you to do the work for me.

---

### Post by rocuan on 2011-04-09
Good idea! I think I can point you in the right direction. 

To tie script to a hot-key / **keyboard shortcut**:
-  System->Preferences->Keyboard Shortcuts
- click add 
- give it  the full path -> (ie) "perl /home/me/bin/wallswap.pl"

To run script at **start up / login** :
- Main Menu -> System -> Preferences -> Startup Applications
- click Add
- give it a name
- in the command box use full path to the script ( perl /home/user/bin/wallswitch.pl )

To run script at **screensaver start / stop** :
- You need to build another perl script to sit around and "listen" for the screensaver signal
- Follow this guide : [http://superuser.com/questions/166232/running-a-program-when-screen-is-unlocked-automatically-ubuntu](http://superuser.com/questions/166232/running-a-program-when-screen-is-unlocked-automatically-ubuntu)
- substitute the following to either the **if **or **elsif** statement ( less latency if you add to if )
```
system( "/usr/bin/perl path_to_your_perl_script" );

```- test the script with two terminal windows & activate the gnome screensaver via command line :
```
 gnome-screensaver-command --activate
```- add the listen script to start-up via: Main Menu -> System -> Preferences -> Startup Applications

To run script at **wake-up** :
   [COLOR=DarkRed]note: [COLOR=Black]I have not got this to work on my hardware[/COLOR][/COLOR] ( acer aspire 5532 POS, Lucid 10.04 )
- You need to add a bash script to /etc/pm/sleep.d/
- Follow this guide : [http://ubuntuforums.org/showthread.php?t=1484156](http://ubuntuforums.org/showthread.php?t=1484156)
- Substitute > /etc/init.d/icecast2 restartwith ```
/usr/bin/perl path_to_your_perl_script
```[COLOR=DarkRed]caution : [COLOR=Black]modifying the /etc/pm/sleep.d/ folder incorrectly WILL corrupt your system.[/COLOR][/COLOR]

---

### Post by rocuan on 2011-04-11
started a new thread on changing the background image at system wakeup [http://ubuntuforums.org/showthread.php?p=10663041](http://ubuntuforums.org/showthread.php?p=10663041)

---

### Post by N33k on 2011-04-11
Appreciate the help, and I'll be eagerly following your new thread, too.

---

