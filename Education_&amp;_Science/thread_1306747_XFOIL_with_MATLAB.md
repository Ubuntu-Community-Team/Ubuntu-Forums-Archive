---
title: "XFOIL with MATLAB"
date: 2009-10-30
forum: Education &amp; Science
---

### Post by azredwing on 2009-10-30
Hi all,

I am trying to write a code in MATLAB that would be able to call up XFOIL from the MATLAB shell and have it run simulations. The closest I can get to doing so is writing a Perl wrapper to take inputs, generate a config file for XFOIL to use, then have XFOIL load it.

The issue is, I plan on many many iterations of this, and there's no "scripting language" within XFOIL to write an XFOIL script. I don't want to have to manually type in "oper; iter 100; alfa _____" for as many iterations as I need. The idea was something like this:

```

while (answer == unconverged)
    use initial guess/previous iteration to  generate config file for XFOIL
    open XFOIL, load config file
    have XFOIL automatically generate CL, CD, other data
    return values back to MATLAB
end

```

Is there any way to get XFOIL to run these commands with having to manually type them in?

Thanks for the help!

---

### Post by XCan on 2009-10-30
I don't know what XFOIL is and I've no clue if what I'm going to suggest will help you, but can't hurt to try. :) 

You can easily start up external apps using the 'system' command in matlab. Depending on your output, you may be able to grab the results from your xfoil app. However, I guess xfoil dumps its data somewhere. Which in that case you can simply let matlab import the data and do your convergence analysis.

---

### Post by azredwing on 2009-10-31
> **XCan said:**
> I don't know what XFOIL is and I've no clue if what I'm going to suggest will help you, but can't hurt to try. :) 

You can easily start up external apps using the 'system' command in matlab. Depending on your output, you may be able to grab the results from your xfoil app. However, I guess xfoil dumps its data somewhere. Which in that case you can simply let matlab import the data and do your convergence analysis.

I am very familiar with the system() command, and so far that is how I'm accessing XFOIL.

XFOIL is a computational fluid dynamics tool used to calculate boundary layers and pressure distributions along airfoil (2D wings). The issue that I am having is that a user needs to run an xfoil "shell" to interact with it. This wouldn't be a problem, since MATLAB is the same way - except with MATLAB, you can write scripts to automate these processes. XFOIL has no way for a user to just run a bunch of commands without having the user actually interact with XFOIL.. i'm not worried about capturing the outputs of XFOIL, that's relatively simple.

---

### Post by udai87 on 2009-12-01
Hey, did you find a solution for your problem? I am also trying to use Xfoil via MATLAB. How do you check if your results are converged?

---

### Post by azredwing on 2009-12-01
> **udai87 said:**
> Hey, did you find a solution for your problem? I am also trying to use Xfoil via MATLAB. How do you check if your results are converged?

I did, actually! I totally forgot that you could use pipes in/out of files, so I have a Perl script generating an XFOIL "script" that gets executed. Here's the code of interest:

```

#!/usr/bin/perl

# xfoilwrapper.pl - Wrapper script to interact between MATLAB, XFOIL

use strict;
use warnings;

sub cleandie{
    unlink $_ for qw(commands.xfoil coords.dat xfoil.def coeffs.txt);
	die @_;
}
	
sub cleanup{
    unlink $_ for qw(commands.xfoil coords.dat xfoil.def coeffs.txt);
}

my ($alfa, $Re, $Ma, $NACA, $coeff_type) = @ARGV;

# If the user wants a NACA foil, make sure it's a 4 or 5-series only.
if (defined $NACA && (length($NACA) <4 || length($NACA) >5 ||  $NACA =~ /\D+/)){
    die "Only 4 or 5-digit series NACA foils allowed";
}


my $Re_10e6 = $Re/10**6; # Config file accepts Re/10^6 as input; need to transform it.

$Re_10e6 = sprintf("%.4f", $Re_10e6);
$Ma      = sprintf("%.4f", $Ma);

#--------------------------------------------------  
# Generate the coordinate files (see end of program)
#--------------------------------------------------  
open my $COORDINATES, ">", "coords.dat"
    or cleandie "Couldn't open coords.dat for writing: $!";

my $coords = get_coords();
print {$COORDINATES} $coords;
close $COORDINATES;

#--------------------------------------------------
# Build the config file using input $Re, $Ma
#--------------------------------------------------

my $xfoil_def = <<"EOF";
  160       1.0000   0.1500   0.2000 | Npan    PPanel  TErat  REFrat
    1.0000   1.0000   1.0000   1.0000 | XrefS1  XrefS2  XrefP1 XrefP2
   10.0000   0.5500   0.0150   0.8000 | Size    plotAR  CHsize ScrnFr
   11.0000   8.5000   0.0000   0.0000 | Xpage   Ypage   Xmargn Ymargn
  F        T                          | Lcolor  Lcursor
    1.0000  -4.0000  -0.5000          | CPmax   CPmin   CPdel
    0.0900   0.7000   0.0200          | XoffAir ScalAir BLUwt
    0.0000   1.5000   0.5000          | CLmin   CLmax   CLdel
    0.0000   0.0400   0.0100          | CDmin   CDmax   CDdel
   -4.0000  10.0000   2.0000          | ALmin   ALmax   ALdel
   -0.2500   0.0000   0.0500          | CMmin   CMmax   CMdel
   1         $Ma   0.0100          | MAtype  Mach    Vaccel
   1         $Re_10e6   9.0000          | REtype  Re/10^6 Ncrit
    0.1000   0.2500                   | XtripT  XtripB
EOF

open my $XFOIL_DEF, ">", "xfoil.def"
    or cleandie "Couldn't open xfoil.def for writing: $!";
print {$XFOIL_DEF} $xfoil_def;
close $XFOIL_DEF;

# Build the XFOIL command list using $alfa and $Re.
# Start with 100 iterations; if the output result is a diverage, add 100 more iterations.
# die() the program after 1000 iterations fail.

my $numit = 100;
ITERATION:
while ($numit <= 1000){
    my $command_file = defined $NACA ? <<"EOF"
y
plop
G

naca $NACA
oper
visc $Re
iter $numit
pacc
coeffs.txt

alfa $alfa
pacc

quit
EOF
      : <<"EOF";
y
plop
G

oper
visc $Re
iter $numit
pacc
coeffs.txt

alfa $alfa
pacc

quit
EOF
      
    open my $COMMANDS, ">", "commands.xfoil"
        or cleandie "Couldn't open commands.xfoil for writing: $!";
    print {$COMMANDS} $command_file;
    close $COMMANDS;

    
    if ($^O eq "linux" || $^O eq "darwin"){
        if ($NACA){
            system("xfoil <commands.xfoil >/dev/null");
        }
        else{
            system("xfoil coords.dat <commands.xfoil >/dev/null");
        }
    }
    else{
        if ($NACA){
            system('C:\xfoil\bin\xfoil.exe <commands.xfoil >nul');
        }
        else{
            system('C:\xfoil\bin\xfoil.exe coords.dat <commands.xfoil >nul');
        }
    }

    # Check coeffs.txt for CL and CD. If there's no numbers, divergence occurred.

    open my $COEFF_FILE, "<", "coeffs.txt"
        or cleandie("Couldn't open coeffs.txt for reading: $!");

    while (my $line = <$COEFF_FILE>){        
        # CONVERAGE OCCURED! PRINT CL AND CD, RETURN TO MATLAB
        if ($line =~ /(\d+[.]\d+) \s+ (\d+[.]\d+) \s+ (\d+[.]\d+)/xms){
            print $coeff_type eq "lift" ? "CL=$2;\n"       :
                  $coeff_type eq "drag" ? "CD=$3;\n"       :
                                          "CL=$2; CD=$3;\n";
            cleanup();
			unlink("coeffs.txt");
            exit
        }
    }
    $numit += 100;
	close $COEFF_FILE;
}

# At this point we've failed to converge after 1000 iterations. Return inf to caller and let the caller deal with what to do.
cleanup();
print "CL=inf;CD=inf;\n";


sub get_coords{
    my $coords = <<"EOF";
# Coordinates for your airfoil go here
EOF
    return $coords;
}

```

And here's the MATLAB function calling this wrapper:

```

% get_coeffs - Get the lift and drag coefficients for an airfoil
%
% USAGE: [CL, CD] = get_coeffs(alfa, Re, Ma, [NACA])
%    (r) alfa: Desired angle of attack 
%    (r)  Re : Reynolds number
%    (r)  Ma : Mach number
%    (s) NACA: NACA Airfoil designation. Must be a 4- or 5-digit string only.

function [CL,CD] = get_coeffs(alfa, Re, Ma, NACA)
    
    % perl() command expects all arguments to be strings - transform into strings... 
    alfa = sprintf('%.5f', alfa);
    Re   = sprintf('%d'  , Re);
    Ma   = sprintf('%0.5f', Ma);
    
    % Result of the eval() command is CL and CD.
    if (exist('NACA') && ~ isempty(NACA))
        eval(perl('xfoilwrapper.pl', alfa, Re, Ma, NACA));
    else
        eval(perl('xfoilwrapper.pl', alfa, Re, Ma));
    end
    
    % In Windows, xfoilwrapper.pl fails to unlink coeffs.txt. Take care of
    % it here.
    if (exist('coeffs.txt'))
        delete('coeffs.txt');
    end

```

Note in the XFOIL wrapper that if divergence occurs, I return CL=inf, CD=inf, and these will be what the MATLAB function returns as well. So you need to check your return vals and have some kind of error catching in place. If I generate CL/CD data and there's holes in it (inf's), I kick the holes out and perform a spline interpolation to fill those holes back in:

```


if (y_of_interest(i) == inf)
     y_of_interest(i) = fill_gaps(x_of_interest, y_of_interest, i);
end

function yy = fill_gap(x,y,i)
    y_interp = [y(1:i-1) y(i+1:length(x))];
    x_interp = [x(1:i-1) x(i+1:length(x))];
    yy = interp1(x_interp, y_interp, x(i), 'spline');
end

```

Hope this helps!

---

### Post by swiftarrow on 2010-02-05
Hi!

I'm designing a windmill for my Mechanical Engineering undergrad project, and I think this may help me.  What I want to do is this:

1. Choose six or seven standard profiles at specific lengths across the blade.
2. Calculate the Cd and Cl for the design Tip speed ratio (or design windspeed) for the entire blade.  This should involve:
  - Calculating Cd and Cl for each Blade Element at design wind speed using XFOIL.
  - Integrating over the blade (is this correct?).
3. Calculate Cd and Cl over a range of windspeeds for the entire blade (perhaps an iteration of steps in two above).
4. Introduce an additional blade angle of twist to make the blade stall in higher speeds, and re-calculate the Cd, Cl for the above.  This will have the effect of changing the Angle of Attack across the blade.

I think your script is a good starting point, however, I'm completely new to XFOIL, python, matlab, and pearl.  (New as in, haven't even run Hello World yet).  I'm pretty sure I can adopt your matlab code to python though.

I'm confused on a few things:

1. Does the above list seem to miss anything?
2. I don't understand the XFOIL interface... help here is very much appreciated.
3. Using your scripts produce a bunch of files.  How do I find the Cd and Cl of my profile under the conditions specified?

Thanks so much!

---

### Post by azredwing on 2010-02-05
> **swiftarrow said:**
> Hi!

I'm designing a windmill for my Mechanical Engineering undergrad project, and I think this may help me.


Lucky for you, this is exactly what I'm doing for my undergraduate project as well! (Actually I'm building a vertical axis wind turbine, but of course this doesn't matter for XFOIL.)

> 
 What I want to do is this:
1. Choose six or seven standard profiles at specific lengths across the blade.
2. Calculate the Cd and Cl for the design Tip speed ratio (or design windspeed) for the entire blade.  This should involve:
  - Calculating Cd and Cl for each Blade Element at design wind speed using XFOIL.
  - Integrating over the blade (is this correct?).
3. Calculate Cd and Cl over a range of windspeeds for the entire blade (perhaps an iteration of steps in two above).
4. Introduce an additional blade angle of twist to make the blade stall in higher speeds, and re-calculate the Cd, Cl for the above.  This will have the effect of changing the Angle of Attack across the blade.


I haven't done a lot of work with XFOIL for 3D airfoils, and as far as I know it can only handle 2D profiles. Like I said, though, I'm not sure. For my 3D model, I am capturing CL/CD as a function of both angular position and height of the blade. The local Reynolds numbers are different as you move across the blade, so finding CL/CD for each "blade element" basically translates to "plugging in the correct alfa and Re". Other than that, the logic sounds good.

> 
I think your script is a good starting point, however, I'm completely new to XFOIL, python, matlab, and pearl.  (New as in, haven't even run Hello World yet).  I'm pretty sure I can adopt your matlab code to python though.

I'm confused on a few things:

1. Does the above list seem to miss anything?
2. I don't understand the XFOIL interface... help here is very much appreciated.
3. Using your scripts produce a bunch of files.  How do I find the Cd and Cl of my profile under the conditions specified?

Thanks so much!

First of all, it's **Perl** and not "pearl" :) 

1) See above for comments on your methodology.
2) Check out the XFOIL manual here: [http://web.mit.edu/drela/Public/web/xfoil/xfoil_doc.txt](http://web.mit.edu/drela/Public/web/xfoil/xfoil_doc.txt)

There are various tutorials on the web, as well. If you look in my Perl script, I have a list of commands that gets piped into XFOIL. This will calculate a single CL/CD given an alfa. 

3) The Perl script is not meant to be run on its own, it should be called from MATLAB. XFOIL generates the CL/CD-alfa data and this data is parsed by the Perl script. The wrapper will clean up after itself and pipe CL/CD back to MATLAB, so there isn't any need to interact with the files Perl or XFOIL generates. (If you're trying to use SciPy/some other language you will need to adopt the MATLAB script into that language, but the Perl wrapper shouldn't change much, if at all.)

Let me know if you've got other questions! Hope I could help.

---

### Post by nikolhs on 2010-05-26
hello guys, i am a new member and i 'd like to ask if you know how can i attach a .txt file (which includes all commands needed for xfoil) in matlab and secondly how can i make matlab iterate a parameter.for example, i have created .txt file :
naca0012
oper
visc
3e4
mach0.3
alfa0
cpwr
example

quit
how can i make matlab run this file from xfoil and how can i write a "for...end" command in matlab in order to change apha from 0 to 5 with step 1. if you could write down all commands needed in matlab it would be really appreciated . thnx

---

### Post by azredwing on 2010-05-29
> **nikolhs said:**
> hello guys, i am a new member and i 'd like to ask if you know how can i attach a .txt file (which includes all commands needed for xfoil) in matlab and secondly how can i make matlab iterate a parameter.for example, i have created .txt file :
naca0012
oper
visc
3e4
mach0.3
alfa0
cpwr
example

quit
how can i make matlab run this file from xfoil and how can i write a "for...end" command in matlab in order to change apha from 0 to 5 with step 1. if you could write down all commands needed in matlab it would be really appreciated . thnx

Edit the MATLAB and Perl scripts I already wrote, above. There's only some minor tweaking that needs to be done.

---

### Post by nikolhs on 2010-06-01
hello,
the code which is above ( Perl script generating an XFOIL script) doesn't run with matlab.When i paste it in a blank .m file, they appear many red marks, which means that's something wrong happens.
If you could explain what exactly i should do (and by this i mean the correct sequence of the files that i have to create etc) i would be really grateful.

---

### Post by azredwing on 2010-06-01
> **nikolhs said:**
> hello,
the code which is above ( Perl script generating an XFOIL script) doesn't run with matlab.When i paste it in a blank .m file, they appear many red marks, which means that's something wrong happens.
If you could explain what exactly i should do (and by this i mean the correct sequence of the files that i have to create etc) i would be really grateful.

The Perl script should be in a .pl file, not a .m file. The MATLAB command to run the Perl script is perl(), and the m-file you create will be calling perl() to run the Perl script. Run help perl at the MATLAB command line for more information.

---

### Post by nikolhs on 2010-06-03
hi,
i have created a .pl file includes the code that begins with:  [FONT=monospace]" [/FONT]#!/usr/bin/perl  " and one other .m file (the matlab function calling the wrapper) but when i run the .m file it appears this message : 
Input argument "alfa" is undefined.

Error in ==> codexfoil at 12
    alfa = sprintf('%.5f', alfa);

is't it already defined ? what should i do ? i suspect that this problem will arise for the other variables too (mach etc)...please reply:confused:

---

### Post by nikolhs on 2010-06-03
what is more, xfoilP4.exe should be in the same folder with the previous files?please answer both...

---

### Post by kazz81 on 2010-06-07
Dear all, 

I'm facing exactly the same problem with Nikolhs. Also, now i have to xfoilwrapper.pl and get_coeff.m, but when i tried running it, i got this msg:

System error: Can't locate warnings.pm in @INC   in Matlab.

I have no knowledge in perl at all...Would you plzz tell us exactly what to do?


Thanks sooooo much in advance

---

### Post by azredwing on 2010-06-08
> **nikolhs said:**
> hi,
i have created a .pl file includes the code that begins with:  [FONT=monospace]" [/FONT]#!/usr/bin/perl  " and one other .m file (the matlab function calling the wrapper) but when i run the .m file it appears this message : 
Input argument "alfa" is undefined.

Error in ==> codexfoil at 12
    alfa = sprintf('%.5f', alfa);

is't it already defined ? what should i do ? i suspect that this problem will arise for the other variables too (mach etc)...please reply:confused:

Hi nikolhs,

The M-file is a function, and notice that its first argument is alfa. You need to supply the input arguments to the function.

Read the first comments in get_coeffs.m to understand the exact syntax needed.

> **nikolhs said:**
> what is more, xfoilP4.exe should be in the same folder with the previous files?please answer both...

So I suppose you're using Windows, then? Note that the code was built for Linux and as such I can't guarantee that it'll work in Windows. If you look at the Perl code, you'll see that it expects the location of the executable to be at C:\xfoil\bin\xfoil.exe .

---

### Post by azredwing on 2010-06-08
> **kazz81 said:**
> Dear all, 

I'm facing exactly the same problem with Nikolhs. Also, now i have to xfoilwrapper.pl and get_coeff.m, but when i tried running it, i got this msg:

System error: Can't locate warnings.pm in @INC   in Matlab.

I have no knowledge in perl at all...Would you plzz tell us exactly what to do?


Thanks sooooo much in advance

Hi kazz81,

What version of MATLAB are you using? I also suppose that you're running Windows, since MATLAB for Linux uses the Perl implementation that comes stock with the OS. In any case, try putting a # in front of the line:
```

use warnings;

```

This will prevent Perl from loading the apparently non-existent "warnings" module and bombing out. 

I just tried running a rudimentary Perl script using MATLAB for Windows, though, and it worked fine.

---

### Post by azredwing on 2010-06-08
If there's enough interest, I could rewrite these scripts to be more general-purpose and have standard releases or something; I suppose aerospace engineers don't typically have the programming skills required to do this type of stuff. Let me know if you'd like to see this.

---

### Post by kazz81 on 2010-06-12
Hey azredwing, 

Thank u very much for your help...

I've tried putting # in front of "use warnings", and that worked ok, but then these lines occured:

??? Error using ==> perl
System error: Too many arguments for open at xfoilwrapper.pl line 34, near "or"
Too many arguments for open at xfoilwrapper.pl line 62, near "or"
Too many arguments for open at xfoilwrapper.pl line 108, near "or"
Too many arguments for open at xfoilwrapper.pl line 133, near "or"
Execution of xfoilwrapper.pl aborted due to compilation errors.
Command executed: perl xfoilwrapper.pl 10.00000 3000000 1.00000 0012

I have no idea what happened here....

Your help would be much appreciated.. thank u again!

(P.S. About the general purpose code that you said you would write?, would 2 interests be enough..me and nikolhs? :D )

---

### Post by azredwing on 2010-06-12
> **kazz81 said:**
> Hey azredwing, 

Thank u very much for your help...

I've tried putting # in front of "use warnings", and that worked ok, but then these lines occured:

??? Error using ==> perl
System error: Too many arguments for open at xfoilwrapper.pl line 34, near "or"
Too many arguments for open at xfoilwrapper.pl line 62, near "or"
Too many arguments for open at xfoilwrapper.pl line 108, near "or"
Too many arguments for open at xfoilwrapper.pl line 133, near "or"
Execution of xfoilwrapper.pl aborted due to compilation errors.
Command executed: perl xfoilwrapper.pl 10.00000 3000000 1.00000 0012

I have no idea what happened here....

Your help would be much appreciated.. thank u again!


Again, what version of MATLAB are you running, and on what OS? It looks like your Perl interpreter is an older one, that doesn't support the relatively more recent 3-argument version of open(). (Now that I think of it, this is probably why use warnings; threw an error as well.)

> 
(P.S. About the general purpose code that you said you would write?, would 2 interests be enough..me and nikolhs? :D )

I am working on it :) The lab that I work in is also pretty interested in this... I can't say it'll be out any time soon, but I am definitely going to do it.

---

### Post by kazz81 on 2010-06-13
Hey azredwing,

I"m running Matlab 7.0 on window xp. and since i don't know Perl at all,
I also have ActivePerl 5.9.9 build 519 installed, but when i copied your
Perl code, i did it in notepad and save it as .pl

Do I need to update my matlab or anything?

Thanks in advance.

---

### Post by nikolhs on 2010-06-13
hello azredwing,
 First of all: yes i 'm using windows.
 Secondly, i would be very interested in the scripts you told so when you finish them let us know...
Finally what you said before isn't clear to me...How can i supply input arguments to the function ? and one more...
what is the file " coeffs.txt " in the end of the .m file? is automatically created or should i create it ?if i have to create it what should i write in ?

---

### Post by azredwing on 2010-06-13
> **kazz81 said:**
> Hey azredwing,

I"m running Matlab 7.0 on window xp. and since i don't know Perl at all,
I also have ActivePerl 5.9.9 build 519 installed, but when i copied your
Perl code, i did it in notepad and save it as .pl

Do I need to update my matlab or anything?

Thanks in advance.

In a MATLAB prompt, run:

```

!perl -v

```

What is the output?

Since you've got ActivePerl installed, you could change MATLAB's PATH to use that Perl interpreter instead of the one built-in. Upgrade to ActivePerl 5.10, then follow the directions here:

[http://home.online.no/~pjacklam/matlab/doc/perl/](http://home.online.no/~pjacklam/matlab/doc/perl/)

---

### Post by azredwing on 2010-06-13
> **nikolhs said:**
> hello azredwing,
 First of all: yes i 'm using windows.
 Secondly, i would be very interested in the scripts you told so when you finish them let us know...
Finally what you said before isn't clear to me...How can i supply input arguments to the function ? and one more...
what is the file " coeffs.txt " in the end of the .m file? is automatically created or should i create it ?if i have to create it what should i write in ?

The code should be run like:

```

[CL, CD] = get_coeffs(alfa, Re, Ma, [NACA])

```

so say I want to analyze a NACA 0021 airfoil at 3.5 degrees AoA, with a Mach number of 0.05 and a Reynolds number of 500,000:

```

[CL, CD] = get_coeffs(3.5, 500000, 0.05, '0021')

```

(Note that you can figure this out if you read the comments in the m-file code!)

As for coeffs.txt: don't create it. The Perl script generates this file, but for some reason the interpreter that ships with MATLAB doesn't clean it up. I end up doing it in MATLAB instead of Perl (which isn't the nicest way to do it - and I'll be cleaning this up in my next version of the code.)

---

### Post by nikolhs on 2010-06-13
it's me again...
i have changed it : 
function [CL,CD] = get_coeffs(1, 10000, 0.3, '0012')
but the line which incudes this gets red and it says:
invalid syntax at '1'.Possibly, a),}, or] is missing
parse error at ')':usage might be invalid MATLAB syntax
so when i run it appears: un expected matlab expression... do you know what have i done wrong (again)? the values 1,10000 etc only in this line need to replace alfa,Re etc... am i wrong ?

---

### Post by azredwing on 2010-06-13
> **nikolhs said:**
> it's me again...
i have changed it : 
function [CL,CD] = get_coeffs(1, 10000, 0.3, '0012')
but the line which incudes this gets red and it says:
invalid syntax at '1'.Possibly, a),}, or] is missing
parse error at ')':usage might be invalid MATLAB syntax
so when i run it appears: un expected matlab expression... do you know what have i done wrong (again)? the values 1,10000 etc only in this line need to replace alfa,Re etc... am i wrong ?

No no, do NOT adjust the code itself! You should be calling the function from MATLAB, like any other function (fsolve(), ode45(), etc)

---

### Post by nikolhs on 2010-06-13
hi,
so i have the .m file unchanged (exactly the same with what you had attached in the first page) and i write in matlab command window :
[CL, CD] = get_coeffs(1.0, 40000, 0.2, '0012')but then appears the following message :
Undefined function or method 'get_coeffs' for input arguments of type 'double'.

please help... thnx

---

### Post by azredwing on 2010-06-13
> **nikolhs said:**
> hi,
so i have the .m file unchanged (exactly the same with what you had attached in the first page) and i write in matlab command window :
[CL, CD] = get_coeffs(1.0, 40000, 0.2, '0012')but then appears the following message :
Undefined function or method 'get_coeffs' for input arguments of type 'double'.

please help... thnx

Make sure you're currently in the same folder as get_coeffs() in MATLAB, or add the folder to your PATH.

---

### Post by nikolhs on 2010-06-13
i have put in the same folder the .m file and the pl file.i have xfoil in the same path which is referred in the .pl file.what else should i do ? it appears the same message:
 
>> [CL, CD] = get_coeffs(1.0, 40000, 0.3, '0012')
??? Undefined function or method 'get_coeffs' for input arguments of type 'double'.

---

### Post by azredwing on 2010-06-13
> **nikolhs said:**
> i have put in the same folder the .m file and the pl file.i have xfoil in the same path which is referred in the .pl file.what else should i do ? it appears the same message:
 
>> [CL, CD] = get_coeffs(1.0, 40000, 0.3, '0012')
??? Undefined function or method 'get_coeffs' for input arguments of type 'double'.

You're SURE that the MATLAB shell is in the same directory as get_coeffs.m ? Because that's what this error message is saying... if get_coeffs.m isn't in the current folder (default view is on the left side of the screen), it won't work. If it IS, then I'm kind of stuck...

---

### Post by nikolhs on 2010-06-13
what do you mean matlab shell ? how can i be sure for this ?

---

### Post by azredwing on 2010-06-14
> **nikolhs said:**
> what do you mean matlab shell ? how can i be sure for this ?

I can't really help you any more if you don't know the basics of MATLAB. I suggest you find tutorials or something online, because I must make a fundamental assumption that you know how to use MATLAB, scripts, functions, etc., and it seems you don't know how...

---

### Post by nikolhs on 2010-06-14
ok i understand...but i have to confirm that i have fully understand what you have sent:
first of all i create a .pl file called xfoilwrapper (which starts with :" #!/usr/bin/perl "), then i create a .m file called codexfoil.m (starts with "% get_coeffs - Get the lift and drag coefficients for an airfoil") which calls the first one and then i write in command window of matlab: 
>> [CL, CD] = get_coeffs(1.0, 40000, 0.3, '0012'). is that right ? thnx

---

### Post by azredwing on 2010-06-14
> **nikolhs said:**
> ok i understand...but i have to confirm that i have fully understand what you have sent:
first of all i create a .pl file called xfoilwrapper (which starts with :" #!/usr/bin/perl "), then i create a .m file called codexfoil.m (starts with "% get_coeffs - Get the lift and drag coefficients for an airfoil") which calls the first one and then i write in command window of matlab: 
>> [CL, CD] = get_coeffs(1.0, 40000, 0.3, '0012'). is that right ? thnx

Correct - except in MATLAB, the .m file must match the name of the function! So the file MUST be called get_coeffs.m or bad things happen.

---

### Post by nikolhs on 2010-06-14
they didn't have the same name and this was the problem!thanks a lot.
now a new problem appears:
 ??? Error: Unexpected MATLAB operator.

Error in ==> get_coeffs at 18
        eval(perl('xfoilwrapper.pl', alfa, Re, Ma, NACA));

do you have any idea?
what is more i created the .pl file in notepad as kazz81 did.. do i need to follow the steps you told him ? if yes where should i put !perl -v you told him ?

---

### Post by azredwing on 2010-07-02
> **nikolhs said:**
> they didn't have the same name and this was the problem!thanks a lot.
now a new problem appears:
 ??? Error: Unexpected MATLAB operator.

Error in ==> get_coeffs at 18
        eval(perl('xfoilwrapper.pl', alfa, Re, Ma, NACA));

do you have any idea?
what is more i created the .pl file in notepad as kazz81 did.. do i need to follow the steps you told him ? if yes where should i put !perl -v you told him ?

Hi nikolhs,

Just type !perl -v into the command window and paste your results back here. As for the error: Can you show me exactly how you're calling the function?

---

### Post by nikolhs on 2010-07-04
hi azredwing,
 this is how i am calling the function :

>> get_coeffs(2.0, 30000, 0.2, '1112')

and the error that appears is :

??? Error using ==> perl at 82
System error: ’¦ ©&#951;©«&#158;£&#152; ›&#156;¤ &#156;&#949;¤&#152;  ©&#156; &#159;&#946;©&#158; ¤&#152; &#156;¤«¦§&#949;©&#156;  «&#158;¤
&#901;&#152;&#159;¦¨ ©£&#946;¤&#158; › &#152;›¨¦£&#947; ›&#949;©&#901;¦¬.
Couldn't open coeffs.txt for reading: No such file or directory at
xfoilwrapper.pl line 10.
Command executed: perl xfoilwrapper.pl 2.00000 30000 0.20000 1112

Error in ==> get_coeffs at 18
        eval(perl('xfoilwrapper.pl', alfa, Re, Ma, NACA));

 do you have any idea?
as for the perl, when should i type !perl-v (before calling the previous function)?
thanks in advance...

---

### Post by aaepl on 2010-07-04
Hi Folks,
 
I too am interested in getting matlab talking to xfoil. I have worked with PABLO in the past, but XFOIL is industry standard. I too am running windows and matlab 7.4. I'm hitting an error probably due to an old perl version.
 
However, my question is can we get this perl script to also output moment coefficient about the quarter chord and centre of pressure location. I.e expand the matlab function to:
 
[FONT=Courier New][SIZE=2][COLOR=#0000ff][FONT=Courier New][SIZE=2][COLOR=#0000ff][FONT=Courier New][SIZE=2][COLOR=#0000ff]function[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2] [CL,CD, CM, XCP] = get_coeffs(alfa, Re, Ma, NACA)[/SIZE][/FONT][/SIZE][/FONT]

[FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]That would be golden. Furthermore, instead of specifing a NACA string can we make it a pointer to a file of coordinates that XFOIL can read? [/SIZE][/FONT][/SIZE][/FONT]

[FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]If these features can be included that will be one powerful simulation tool![/SIZE][/FONT][/SIZE][/FONT]

[FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]I'll work on this as well and post any progress I make.[/SIZE][/FONT][/SIZE][/FONT]

[FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]Cheers[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Courier New][SIZE=2]
[/SIZE][/FONT]

---

### Post by aaepl on 2010-07-19
Just a quick update, not sure if people are still interested. I got this working on windows. 
 
First thing to do is to install the latest perl. Then when I tried to run the xfoilwrapper an error was thown because MATLAB was still looking at the old perl.exe file. I followed the link into the m file where the error was being hit and editied the path line to point it to the new perl.exe.
 
Next install the latest xfoil.
 
Finally in the xfoilwrapper.pl file locate the function "system", and replace the line with exactly:
 
system("xfoil <commands.xfoil >nul")
 
Also make sure the command list that is being generated is suitable for the xfoil version you are running. Do this by making a copy of commands.xfoil, then manually open xfoil and enter each line of the commands.xfoil file making sure no problems are hit in xfoil.
 
I have changed a lot of things in the xfoilwrapper file to suit my needs, it is not that hard once you get your head around it.
 
Hope that helps.

---

### Post by nikolhs on 2010-07-20
hi aaepl,
when i call the function get_coeffs the message i wrote above appears. do you have any idea?beacause in lines where the problem is ,they aren't the same as yours...
thanks

---

### Post by aaepl on 2010-07-21
> **nikolhs said:**
> hi aaepl,
when i call the function get_coeffs the message i wrote above appears. do you have any idea?beacause in lines where the problem is ,they aren't the same as yours...
thanks
 
Hi Nikolhs,
 
I cant say exactly what your problem is. That error indicates that xfoil has not successfully run. This can be because of a number of things but I am betting that there is a problem in your commands.xfoil file that is being generated (provided it is being generated).
 
What you need to do is prevent the wrapper from deleteing the commands.xfoil file when the erorr is hit (search through the code and you will see what to comment out). Then open the commands.xfoil file and see what has been written. Manually open xfoil and enter each command from the commands.xfoil file manually to try and locate the problem.
 
If there are no problems there then I would suggest that your perl file is not opening xfoil and sending the commands.xfoil file properly. Make sure your 'system' command line is:
 
system("xfoil <commands.xfoil >nul")
 
If everything runs properly a coeff.txt is generated with all the coefficients. I use matlab to open that and parse through it. Thats all I can offer.
 
Cheers.

---

### Post by azredwing on 2010-07-24
Thanks for helping out, **aaepl**. I've been really busy with work and personal stuff, so I've had ZERO time to work on solving this problem. I thought in xfoilwrapper.pl I had a Windows-friendly command, but perhaps it's not right.

In any case, for anyone that can't get this working on Windows, I strongly suggest you change your Perl from the MATLAB-built-in interpreter to using ActivePerl. 

As aaepl said, messing around with the source code in xfoilwrapper.pl isn't too challenging - and if you're comfortable working in MATLAB, you shouldn't be too flummoxed by writing in Perl...

I'm making some progress on the more generalized XFOIL/MATLAB hook, and at some point I might start a SourceForge page or something to make the project larger, should it require that. I don't see it getting that big, since all you need to be able to input is Re, Ma and alfa (and aseq to get a range of alfa), but it would be nice to have others help out. 

I'll keep everyone apprised as I continue. Development is kind of on hold due to issues with my own life that I'm taking care of.

---

### Post by azredwing on 2010-07-24
> **aaepl said:**
> Hi Folks,
 
I too am interested in getting matlab talking to xfoil. I have worked with PABLO in the past, but XFOIL is industry standard. I too am running windows and matlab 7.4. I'm hitting an error probably due to an old perl version.
 
However, my question is can we get this perl script to also output moment coefficient about the quarter chord and centre of pressure location. I.e expand the matlab function to:
 
[FONT=Courier New][SIZE=2][COLOR=#0000ff][FONT=Courier New][SIZE=2][COLOR=#0000ff][FONT=Courier New][SIZE=2][COLOR=#0000ff]function[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2] [CL,CD, CM, XCP] = get_coeffs(alfa, Re, Ma, NACA)[/SIZE][/FONT][/SIZE][/FONT]

[FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]That would be golden. Furthermore, instead of specifing a NACA string can we make it a pointer to a file of coordinates that XFOIL can read? [/SIZE][/FONT][/SIZE][/FONT]

[FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]If these features can be included that will be one powerful simulation tool![/SIZE][/FONT][/SIZE][/FONT]

[FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]I'll work on this as well and post any progress I make.[/SIZE][/FONT][/SIZE][/FONT]

[FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]Cheers[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Courier New][SIZE=2]
[/SIZE][/FONT]

Let me know how far you get - this would be pretty interesting to have and not at all difficult. I basically just grab CL and CD from the output coeffs.txt and pipe that back to MATLAB, but it wouldn't be difficult to make it output CM and XCP either.

As for specifying non-NACA profiles: for right now, I just hardcoded airfoils into xfoilwrapper.pl, but this idea is definitely on the docket.

---

### Post by dewapur on 2010-08-11
Hi all,

I also interested of using matlab with xfoil but I'm not familiar yet with xfoil. I tried azredwing's script and I got CL and CD value as text, few additional matlab command then I got myself CL and CD value as matlab variables. I would like to do modification a NACA model to get best CL. I want xfoil to do the calculation of CL and Matlab do the optimization. Is there a way to do it?

---

### Post by aaepl on 2010-08-11
> **azredwing said:**
> Let me know how far you get - this would be pretty interesting to have and not at all difficult. I basically just grab CL and CD from the output coeffs.txt and pipe that back to MATLAB, but it wouldn't be difficult to make it output CM and XCP either.
 
As for specifying non-NACA profiles: for right now, I just hardcoded airfoils into xfoilwrapper.pl, but this idea is definitely on the docket.
 
Hi azredwing,
 
Yeah I have got this function working. As you say CM is easy enough, and XCP is simply 0.25 - (cm/cl), becasue the moment coefficient is taken about the quarter chord. 
 
As for the aerofoil I have just put a folder of aerofoils that comes with xfoil in the same directory as the perl script. Then in my matlab function I point the script to the files in that folder. That opens up 1500 different aerofoils to use. If you want you can also make your own aerofoils on the fly in matlab, paste them into that same folder and get xfoil to crunch the numbers on them, pretty nifty when you want to linearly interpolate between two aerofoils.
 
With this sort of power, it opens up so many possibilities. For instance I have now made a matlab program that uses xfoil to produce Lift/Drag plots as a function of CL for many different aerofoils all overlaid on the one plot. You can do the same for Cm and Cd, allowing you to rapidly determine the best aerofoils for a given flow condition.
 
I don't have the time or will-power to take this any further, because it has addressed all my needs, but I'll check back here periodically to help out if I can.
 
Cheers

---

### Post by azredwing on 2010-08-20
First of all, I'm glad everyone is so interested in my work. I'm really sorry that I haven't been able to check in here more often to help people out. Quite frankly the code I wrote does its job well enough for me, and I had no idea it would get as popular as it did. I'm thinking of getting a SourceForge page and making this a full-blown project. If there's anyone out there willing to help me out here, let me know - please PM me and we can discuss privately.

> **aaepl said:**
> Hi azredwing,
 
Yeah I have got this function working. As you say CM is easy enough, and XCP is simply 0.25 - (cm/cl), becasue the moment coefficient is taken about the quarter chord. 
 
As for the aerofoil I have just put a folder of aerofoils that comes with xfoil in the same directory as the perl script. Then in my matlab function I point the script to the files in that folder. That opens up 1500 different aerofoils to use. If you want you can also make your own aerofoils on the fly in matlab, paste them into that same folder and get xfoil to crunch the numbers on them, pretty nifty when you want to linearly interpolate between two aerofoils.
 
With this sort of power, it opens up so many possibilities. For instance I have now made a matlab program that uses xfoil to produce Lift/Drag plots as a function of CL for many different aerofoils all overlaid on the one plot. You can do the same for Cm and Cd, allowing you to rapidly determine the best aerofoils for a given flow condition.
 
I don't have the time or will-power to take this any further, because it has addressed all my needs, but I'll check back here periodically to help out if I can.
 
Cheers

I think I've got enough time now to start working on this more generally. Here's the function call for the framework I'm thinking of:

```

function [CL,CD,CM, Xcp] = xfoil(airfoil, Re, Ma, maxit, alfa_start, alfa_end, alfa_step)

```

So you are required to specify airfoil, Re, Ma, and alfa_start; maxit will default to some number, alfa_end and alfa_step are only used when you want to do a MATLAB aseq command, since that's much more efficient than calling this function over and over again in a for loop.

Other ideas for what needs to go in?

Also could you post or send me your modifications? I'd like to incorporate them if they're already working. (Of course when this is released you will get full credit - I'd like to release under the GPL or something.)

---

### Post by azredwing on 2010-08-20
> **dewapur said:**
> Hi all,

I also interested of using matlab with xfoil but I'm not familiar yet with xfoil. I tried azredwing's script and I got CL and CD value as text, few additional matlab command then I got myself CL and CD value as matlab variables. I would like to do modification a NACA model to get best CL. I want xfoil to do the calculation of CL and Matlab do the optimization. Is there a way to do it?

I suppose you could iterate over many airfoils to maximize CL for a particular alfa and Re, but this is really an NP-complete problem: airfoil optimization is extremely difficult computationally and quite frankly XFOIL is not designed to perform airfoil optimization. 

The problem is this: given some starting values of CL for, say, a 4-digit NACA airfoil, how do you determine what to vary? You could increase the camber (first digit), location of camber (second digit), or thickness (final two digits) - but varying these will have effects on CL_0, stall behavior, etc. There's no way to uncouple CL from these other factors on the CL-alfa curve, and there's no clear functional relationship between CL and any of the parameters you could vary in a 4-digit NACA airfoil - and any functional relationship will also be a function of Re and Ma, so you've got to have a very strict flight regime to even think of doing some type of airfoil optimization.

This gets even more complicated using a 5-digit series airfoil, and we're truly in an NP-complete situation when you want to build custom airfoils. Ph.Ds do this with extremely powerful CFD software that is way outside the bounds of my knowledge of the field of aerodynamics. 

If any Ph.Ds want to contribute to the project, contact me :)

---

### Post by azredwing on 2010-08-26
Hi all,

Development is under full swing! Check out [http://sourceforge.net/projects/mpxfoil/](http://sourceforge.net/projects/mpxfoil/) - this will be updated rapidly in the next few days. A release for Linux should be coming up shortly - at this point it's just taking care of setting up svn and doing some legalese stuff.

Windows users need to hold tight - there are several fundamental differences between Linux and Windows that dictate how I control XFOIL. It's proven very difficult to write for Windows, mostly because XFOIL expects a (pseudo)terminal and ptys don't exist in Windows. I'm trying to build a workaround, but there's a chance this utility might not be buildable for Windows in its current form.

---

### Post by azredwing on 2010-09-17
Hi all,

MPXF 0.1 is available for release for Windows, Mac, and Linux! Get it at [https://sourceforge.net/projects/mpxfoil/](https://sourceforge.net/projects/mpxfoil/) .

Read the README. There's some pretty major prerequisites to satisfy if you're running Windows, and a couple Perl modules that everyone needs to have installed to utilize this software. 

Please PM me or email me if you have any questions/comments/concerns/bug reports. I really hope this works out and finally provides the XFOIL/MATLAB interface everyone has been looking for!

---

### Post by Schuifpui2 on 2010-09-18
Hello all,

I'm new here. I study aerospace engineering and for a project I'm trying to optimize an airfoil using MATLAB. I've tried the script posted on the first page of this thread, but it only works partially I think. I don't know anything about perl, so I would appreciate some help here.


It all runs well until the coeffs.txt is created. That seems alright, but MATLAB then gives and error:

> ??? Error: Unexpected MATLAB operator.

Error in ==> get_coeffs at 19
        eval(perl('xfoilwrapper.pl', alfa, Re, Ma, NACA));

Error in ==> test at 9
get_coeffs(alfa, Re, Ma, NACA)If I'm right the problem can only be caused by perl not being able to read the file coeffs.txt properly. I'm guessing it is because I have a different version of Xfoil. The exe file is called XfoilP4.exe, some commands were different too, but I fixed that.

The coeffs.txt file looks like this:

  
>        XFOIL         Version 6.94
  
 Calculated polar for: NACA 0024                                       
  
 1 1 Reynolds number fixed          Mach number fixed         
  
 xtrf =   0.100 (top)        0.250 (bottom)  
 Mach =   0.000     Re =     1.200 e 6     Ncrit =   9.000
  
  alpha     CL        CD       CDp       CM    Top_Xtr Bot_Xtr
 ------- -------- --------- --------- -------- ------- -------
   0.000  -0.0219   0.01241   0.00381   0.0038  0.1000  0.2500Do I need to change something in the part were the script tries to read this file?

I this is not the case, could someone tell what's causing the error?


thanks alot! And indeed if it all works it's very powerful.

---

### Post by azredwing on 2010-09-18
> **Schuifpui2 said:**
> Hello all,

I'm new here. I study aerospace engineering and for a project I'm trying to optimize an airfoil using MATLAB. I've tried the script posted on the first page of this thread, but it only works partially I think. I don't know anything about perl, so I would appreciate some help here.


It all runs well until the coeffs.txt is created. That seems alright, but MATLAB then gives and error:

If I'm right the problem can only be caused by perl not being able to read the file coeffs.txt properly. I'm guessing it is because I have a different version of Xfoil. The exe file is called XfoilP4.exe, some commands were different too, but I fixed that.

The coeffs.txt file looks like this:

  
Do I need to change something in the part were the script tries to read this file?

I this is not the case, could someone tell what's causing the error?


thanks alot! And indeed if it all works it's very powerful.

Check out the post directly above you - it should be a cleaner version of my original script. It does need the XFOIL binary to be named "xfoil.exe" if you're running Windows.

Let me know if MPXF works out. I haven't tested it heavily on Windows.

---

### Post by Schuifpui2 on 2010-09-19
Thanks [azredwing]("http://ubuntuforums.org/member.php?u=546981"),

I didn't notice the post, because it wasn't there on Friday when I started this. I downloaded the packages and did everything in the readme file, but it doesn't work. This is the message I get in MATLAB:

> ??? Error using ==> runperl at 67
Perl binary not found. Install Cygwin with Perl, then add <parent folder>\\cygwin\\bin to your PATH.

Error in ==> mpxfoil at 127
    runperl('xfw.pl', airfoil, isnaca, Re, Ma, alfa_start, alfa_end, alfa_step, maxit, input_file, timeout);

Error in ==> test at 12
mpxfoil(airfoil, Re, Ma, alfa_start, alfa_end, alfa_step, maxit, timeout) The steps I performed:
Installed Cygwin, and enabled complete perl libary, all of the packages starting with gcc and two packages started with make. I added the paths in the windows environment settings. 

The command:
# perl -MCPAN -e "install IO: Pty; install IPC::Run"

does not run in the unix shell. That's the thing that looks like a DOS prompt, right? Sorry I'm an absolute noob with unix, ubuntu. I just want to get the matlab/xfoil interaction working and got here by using google.

Could you give me advice, I would really appreciate it. Thanks a lot already.

---

### Post by Schuifpui2 on 2010-09-19
Alright, I reinstalled everything, including all packages this time. I still get the same error message. Any ideas?

Edit: Forget previous message, I got a bit further. Now I get an error while running the matlab file in black text:

> XFOIL error: Command 'xfoil' not found in /cygdrive/c/Program Files/MATLAB/R2008b/bin/win32, /cygdrive/c/watcom-1.3/binnt, /cygdrive/c/watcom-1.3/binw, /cygdrive/c/Program Files/MiKTeX 2.8/miktex/bin, %CommonProgramFiles%/Microsoft Shared/Windows Live, /cygdrive/c/Windows/system32, /cygdrive/c/Windows, /cygdrive/c/Windows/System32/Wbem, /cygdrive/c/Windows/System32/WindowsPowerShell/v1.0/, /cygdrive/c/Program Files/MATLAB/R2008b/bin, /cygdrive/c/Program Files/MATLAB/R2008b/bin/win32, /cygdrive/c/Program Files/Common Files/DivX Shared/, /cygdrive/c/Program Files/QuickTime/QTSystem/, /cygdrive/c/Program Files/Common Files/Microsoft Shared/Windows Live, /usr/bin, /cygdrive/c/XFOIL/bin at xfw.pl line 81

Any ideas on this? I first thought that it would have something to do with the path thing, but when I change that I always get the message from my previous post. So I think my path thingy in windows is right. This is what I have there:

> %CommonProgramFiles%\Microsoft Shared\Windows Live;C:\cygwin\bin;C:\XFOIL\bin

---

### Post by swimsfast99 on 2010-09-21
Quick question.  Does this perl shell run Xfoil without the plots automatically popping up?  I am trying to figure out a way to run MatLAB and Xfoil together without the plots automatically creating and coming to the front of the desktop.  Currently since this is going on, I cannot run it on any type of server or parallel clusters.  I am trying to pull Cd, Cl, and Cm values from user created airfoils.  

For all of you using windows.  A short-cut to get Xfoil and Matlab running together is actually one simple command:

dos(xfoil.exe < commands.txt)

This assumes that xfoil.exe is in the same folder as where your m file is.  In addition the commands.txt file should contain all of your xfoil commands that you need to run.  This runs perfectly with no problems.  Make sure to start every command on a new line.

---

### Post by azredwing on 2010-09-22
> **Schuifpui2 said:**
> Alright, I reinstalled everything, including all packages this time. I still get the same error message. Any ideas?

Edit: Forget previous message, I got a bit further. Now I get an error while running the matlab file in black text:
> 
XFOIL error: Command 'xfoil' not found in /cygdrive/c/Program Files/MATLAB/R2008b/bin/win32, /cygdrive/c/watcom-1.3/binnt, /cygdrive/c/watcom-1.3/binw, /cygdrive/c/Program Files/MiKTeX 2.8/miktex/bin, %CommonProgramFiles%/Microsoft Shared/Windows Live, /cygdrive/c/Windows/system32, /cygdrive/c/Windows, /cygdrive/c/Windows/System32/Wbem, /cygdrive/c/Windows/System32/WindowsPowerShell/v1.0/, /cygdrive/c/Program Files/MATLAB/R2008b/bin, /cygdrive/c/Program Files/MATLAB/R2008b/bin/win32, /cygdrive/c/Program Files/Common Files/DivX Shared/, /cygdrive/c/Program Files/QuickTime/QTSystem/, /cygdrive/c/Program Files/Common Files/Microsoft Shared/Windows Live, /usr/bin, /cygdrive/c/XFOIL/bin at xfw.pl line 81




Any ideas on this? I first thought that it would have something to do with the path thing, but when I change that I always get the message from my previous post. So I think my path thingy in windows is right. This is what I have there:

[quote]
%CommonProgramFiles%\Microsoft Shared\Windows Live;C:\cygwin\bin;C:\XFOIL\bin

[/QUOTE]

Hi **Schuifpui2**,

You mentioned that you're running "xfoilp4.exe" instead of "xfoil.exe", yes? Try opening up mpxfoil.m and change XFOIL_EXE to "xfoilp4" maybe? Where did you install Cygwin to, and where did you install XFOIL to?

I've been busy the past couple days, sorry for the late replies. Did you get the Perl modules set up okay?

(This is my first time developing for Windows - so I'm sure the process isn't nearly as smooth as I'd like it to be. Thanks for being my guinea pig...)

---

### Post by azredwing on 2010-09-22
> **swimsfast99 said:**
> Quick question.  Does this perl shell run Xfoil without the plots automatically popping up?  I am trying to figure out a way to run MatLAB and Xfoil together without the plots automatically creating and coming to the front of the desktop.  Currently since this is going on, I cannot run it on any type of server or parallel clusters.  I am trying to pull Cd, Cl, and Cm values from user created airfoils.  

For all of you using windows.  A short-cut to get Xfoil and Matlab running together is actually one simple command:

dos(xfoil.exe < commands.txt)

This assumes that xfoil.exe is in the same folder as where your m file is.  In addition the commands.txt file should contain all of your xfoil commands that you need to run.  This runs perfectly with no problems.  Make sure to start every command on a new line.

Hi **swimsfast99**,

My Perl backend disables graphical plotting - I had the same issues you're mentioning: I wanted a way to rapidly iterate over and over on a quad-core computer. If you're running Linux, I can almost guarantee that MPXF will work for you. If you're a Windows user, I can almost guarantee that once everything is set up, MPXF will work for you - since I've never developed for Windows before (and especially since I've never had anyone set up Cygwin before) I'm sure there's a fundamental disconnect between installing things for Windows vs Linux (i.e., you need gcc, perl, make, all of which are available with Linux but take a lot of work in Windows/Cygwin) that I haven't even thought of. If you're a Windows user, I'd very much appreciate if you tried out my script and gave me some feedback.

As for the dos() command: This is essentially what I used to do in my original script in some posts above. I found that this method is not particularly robust for funky AoA or flow regimes - you can hit "!" to continue iterating if the system doesn't converge, but you can't predict that ahead of time. This is what I found with the original version of my script. The pty + Cygwin workaround is so I can make it just as robust as I could with Linux - Windows doesn't support pty natively, so there's no way to interactively watch the STDIN and STDOUT for when the "user" (i.e., parent process) should input a "!" and continue iteration.

---

### Post by Schuifpui2 on 2010-09-23
> **azredwing said:**
> Hi **Schuifpui2**,

You mentioned that you're running "xfoilp4.exe" instead of "xfoil.exe", yes? Try opening up mpxfoil.m and change XFOIL_EXE to "xfoilp4" maybe? Where did you install Cygwin to, and where did you install XFOIL to?

I've been busy the past couple days, sorry for the late replies. Did you get the Perl modules set up okay?

(This is my first time developing for Windows - so I'm sure the process isn't nearly as smooth as I'd like it to be. Thanks for being my guinea pig...)

I renamed XfoilP4 to Xfoil so I assumed that wouldn't be necessary. My xfoil is installed at c:\xfoil, while the readme told me to add C:\xfoil\bin to the path. I think this is the problem. Added c:\xfoil to the path instead of the \bin folder solves this.

As always with computer stuff, when you solve one problem, you are awarded with a new one. I have no clue what this is about, since it probably goes much deeper into the code:

> XFOIL error: alarm

Warning: File 'C:\Users\<USERNAME>\AppData\Local\Temp\tpaa44bbf7_733e_4c1b_a91d_b21bc25dffe3' not found. 
> In mpxfoil at 137
  In test at 12

ans =

   NaN

---

### Post by laneli on 2010-09-23
@ swimsfast99: if you're running xfoil 9.96 or higher you can disable graphics from in the xfoil menu as follows: type

PLOP (for plotting options);
G (for Graphics enable flag -> the value changes to False, type G again and to enable Graphics again);
enter to return to previous menu

or just put

'PLOP'
'G'
' '

at the beginning of your 'Filename.txt'.

Hope that helps!

---

### Post by azredwing on 2010-09-23
> **Schuifpui2 said:**
> I renamed XfoilP4 to Xfoil so I assumed that wouldn't be necessary. My xfoil is installed at c:\xfoil, while the readme told me to add C:\xfoil\bin to the path. I think this is the problem. Added c:\xfoil to the path instead of the \bin folder solves this.


Good to know - thanks. I think my Windows setup uses C:\XFOIL\bin, which is weird. I'll look into this more.

> 
As always with computer stuff, when you solve one problem, you are awarded with a new one. I have no clue what this is about, since it probably goes much deeper into the code:

[quote]
XFOIL error: alarm

Warning: File 'C:\Users\<USERNAME>\AppData\Local\Temp\tpaa44bbf7 _733e_4c1b_a91d_b21bc25dffe3' not found. 
> In mpxfoil at 137
In test at 12

ans =

NaN


[/QUOTE]

Could you provide me the parameters you tried to run on? The alarm error is supposed to be a timeout after 5 minutes, in case XFOIL gets stuck iterating over and over again. All the data is written to a temporary file which is parsed in Perl and sent to MATLAB. I haven't run enough test cases to cover when a timeout occurs, so I'm kind of glad that you ran into this. I had a similar timeout setup on a personal script I wrote to use all 4 cores of my quad-core processor, but I never used it on Windows and my airfoil/settings were relatively sane.

Again, thanks for being my guinea pig. If you ever get sick of it, you could always adapt the scripts in the original post...

---

### Post by Schuifpui2 on 2010-09-23
I don't mind being you guinea pig. If we get it working, you have helped me big time. :)

I ran a simple test file:
> 
airfoil = '0012';
Re = 1200000;
Ma = 0;
alfa_start = 1;
alfa_end = 1;
alfa_step = 1;
maxit = 200;
timeout = 60;

mpxfoil(airfoil, Re, Ma, alfa_start, alfa_end, alfa_step, maxit, timeout)
Also tried different alpha's, but no luck. I also noticed there aren't any files created in the folder itself, is that right? If I remember correctly the code on the first page generated a txt file with the commands, this one doesn't seem to do that. Or is it created in another location? If I have a list of commands that is being send to xfoil, I can check if it works by running them manually.

Xfoil is started correctly, since it shows in the task manager.

---

### Post by azredwing on 2010-09-24
> **Schuifpui2 said:**
> I don't mind being you guinea pig. If we get it working, you have helped me big time. :)

I ran a simple test file:

Also tried different alpha's, but no luck. I also noticed there aren't any files created in the folder itself, is that right? If I remember correctly the code on the first page generated a txt file with the commands, this one doesn't seem to do that. Or is it created in another location? If I have a list of commands that is being send to xfoil, I can check if it works by running them manually.

Xfoil is started correctly, since it shows in the task manager.

Try using alfa_end and alfa_step = [] - it looks like you're trying to do a singleton analysis (only one angle of attack, as opposed to a range.) Let me know if that worked at all - for singleton alfa I just omitted these things entirely..

Also, no commands file is generated now. I am piping commands directly into XFOIL - this lets me robustly detect when non-convergence occurs, so the program can tell XFOIL to keep iterating.

---

### Post by dewapur on 2010-09-24
> **azredwing said:**
> I suppose you could iterate over many airfoils to maximize CL for a particular alfa and Re, but this is really an NP-complete problem: airfoil optimization is extremely difficult computationally and quite frankly XFOIL is not designed to perform airfoil optimization. 

The problem is this: given some starting values of CL for, say, a 4-digit NACA airfoil, how do you determine what to vary? You could increase the camber (first digit), location of camber (second digit), or thickness (final two digits) - but varying these will have effects on CL_0, stall behavior, etc. There's no way to uncouple CL from these other factors on the CL-alfa curve, and there's no clear functional relationship between CL and any of the parameters you could vary in a 4-digit NACA airfoil - and any functional relationship will also be a function of Re and Ma, so you've got to have a very strict flight regime to even think of doing some type of airfoil optimization.

This gets even more complicated using a 5-digit series airfoil, and we're truly in an NP-complete situation when you want to build custom airfoils. Ph.Ds do this with extremely powerful CFD software that is way outside the bounds of my knowledge of the field of aerodynamics. 

If any Ph.Ds want to contribute to the project, contact me :)
yeah, mapping CL and CD over some airfoil is what I'm trying to do. I let XFOIL to calculate CL and CD over some airfoil (4-digit NACA) and Matlab handle the flow. The calculation is done with some limitation range of camber, camber position, thickness and alfa but Re is fixed. It went stuck on the way to calculate an airfoil, for example NACA 6807 with alfa 3. I tried directly the airfoil with XFOIL and it converged, so it means should have no problem. Is XFOIL have limitation over memory it can handle?

btw, what is NP-complete problem? unluckily I'm no Ph.D student yet :)

---

### Post by Schuifpui2 on 2010-09-27
Sorry for the late reply, I wasn't at home this weekend. The same problem arises for a range of alpha.

---

### Post by azredwing on 2010-09-30
> **Schuifpui2 said:**
> Sorry for the late reply, I wasn't at home this weekend. The same problem arises for a range of alpha.

Thanks for confirmation - I'll take a look this weekend. I've got lots of ideas for the next iteration of this project, but usage is absolutely #1 on the list.

---

### Post by bmuyl on 2010-10-07
azredwing,
Looks like a great tools.
I am facing the following issue.
I am using mac os x.
I followed the read me instructions.

When I use mpxfoil i get the following error message:

Can't open perl script "xfw.pl": No such file or directory
Warning: File '/tmp/tp7e2af119_5d89_4360_84e8_4c9ddfe8784c' not found.
> In mpxfoil at 137
 

The script xfw.pl is in the same directory as mpxfoil.
Any clue on what the issue could be ? 

Thanks

---

### Post by azredwing on 2010-10-11
> **bmuyl said:**
> azredwing,
Looks like a great tools.
I am facing the following issue.
I am using mac os x.
I followed the read me instructions.

When I use mpxfoil i get the following error message:

Can't open perl script "xfw.pl": No such file or directory
Warning: File '/tmp/tp7e2af119_5d89_4360_84e8_4c9ddfe8784c' not found.
> In mpxfoil at 137
 

The script xfw.pl is in the same directory as mpxfoil.
Any clue on what the issue could be ? 

Thanks

Hi **bmuyl**:

I don't have any experience with Macs so this is gonna be a bit difficult to do for me. But, I think I can see what the problem is. From what directory are you calling the mpxfoil function? I have a feeling that you're in a different directory than where mpxfoil.m is located - I use relative paths to call xfw.pl. Try setting your current directory to be the same directory as mpxfoil.m and see what happens.

TO ALL: I am having a very difficult time keeping up with my school work and managing this project. If anyone is interested in helping me develop these tools, please let me know.

---

### Post by bmuyl on 2010-10-11
azredwing

Thanks ! 
Was as easy as that.

Cheers

---

### Post by bmuyl on 2010-10-11
azredwing,
I have now xfw.pl found by mpxfoil.m
and I have added xfoil path to matlab so that xfw.pl finds it.
That is working as mpxfoil opens an xfoil window ( would be great to avoid that, by the way..)
 
But I get the following message:

>> mpxfoil('6312', 3000000, 0, 500, 0)
XFOIL error: process ended prematurely at xfw.pl line 98

Warning: File '/tmp/tpdf8119d4_c602_49f1_8ba4_10b757937def' not found.
> In mpxfoil at 147

ans =

   NaN


Line 98, is the following one:

			$h->pump;




Any clue ? 
Thanks

Benjamin

---

### Post by elmanuelito on 2011-02-12
Hi
Just a short question: why do you use a perl wrapper?

It seems to me that everything can be done within matlab: writing a list of command for xfoil  in a file input.in and calling xfoil with:  system('/path/to/xfoil/xfoil < input.in')

I haven't tried, but doesn't this work on windows? 
Do you want to make this portion of code independent of matlab to use it with other languages like python or with a shell script?

In advance, thanks for your clarification

---

### Post by azredwing on 2011-02-12
> **elmanuelito said:**
> Hi
Just a short question: why do you use a perl wrapper?

It seems to me that everything can be done within matlab: writing a list of command for xfoil  in a file input.in and calling xfoil with:  system('/path/to/xfoil/xfoil < input.in')

I haven't tried, but doesn't this work on windows? 
Do you want to make this portion of code independent of matlab to use it with other languages like python or with a shell script?

In advance, thanks for your clarification

Hi **emanuelito**:

The main reason why I use the Perl wrapper is because I use psuedo-ttys to catch when XFOIL fails to iterate and needs to manually have the user enter a '!' to continue iterating. As far as I know this isn't possible with MATLAB alone. (Really, you could use Python or any shell script you'd like - the Perl wrapper I wrote makes it very easy to run pseudotty.)

I used to simply build the list of commands like you've got written, but the system ends up just waiting for a '!' that will never come if you do it naively. You can't know in advance when you'll need a '!' which is why I have Perl check. I can read the ptty in real time from XFOIL.

---

### Post by azredwing on 2011-02-17
> **elmanuelito said:**
> Hi
Just a short question: why do you use a perl wrapper?

It seems to me that everything can be done within matlab: writing a list of command for xfoil  in a file input.in and calling xfoil with:  system('/path/to/xfoil/xfoil < input.in')

I haven't tried, but doesn't this work on windows? 
Do you want to make this portion of code independent of matlab to use it with other languages like python or with a shell script?

In advance, thanks for your clarification

Now that I think about it (this probably won't help for you), you can bypass the Perl script because MATLAB can leverage *NIX's popen() functionality via this module: [http://www.mathworks.com/matlabcentral/fileexchange/13851](http://www.mathworks.com/matlabcentral/fileexchange/13851)

To keep the program platform independent (even though really the Windows version is just a hack), I use the Perl backend.

---

### Post by azredwing on 2011-02-17
> **bmuyl said:**
> azredwing,
I have now xfw.pl found by mpxfoil.m
and I have added xfoil path to matlab so that xfw.pl finds it.
That is working as mpxfoil opens an xfoil window ( would be great to avoid that, by the way..)
 
But I get the following message:

>> mpxfoil('6312', 3000000, 0, 500, 0)
XFOIL error: process ended prematurely at xfw.pl line 98

Warning: File '/tmp/tpdf8119d4_c602_49f1_8ba4_10b757937def' not found.
> In mpxfoil at 147

ans =

   NaN


Line 98, is the following one:

			$h->pump;




Any clue ? 
Thanks

Benjamin


Whoa - I never saw this post. Sorry I didn't help out sooner! I feel bad.

Looks like you're trying to use an alfa_start of 500 deg?? I can't blame XFOIL for crashing out (which it looks like happened).

---

### Post by rheaseo25 on 2011-06-16
Such as a great information on how work on XFOIL and MATLAB.

i bookmark this page for future reference: thanks;)

---

### Post by Estebanvt on 2012-01-29
Hi azredwing,

I have Ubuntu, and I installed from ubuntu software center Xfoil 6.97, and Matlab 2011a. I want to use xfoil from matlab and get the results of boundary layer and separation in matlab. I saw your code mxfoil, and I copied all the files that you mentioned. I create finally another file to call mpxfoil with the following data:


[alfa, CL, CD, CDp, CM, Top_Xtr, Bot_Xtr] = mpxfoil('0012', 500000, 0.2,0.2,[], [], [],[])

And I get the following error:

Can't locate IPC/Run.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at xfw.pl line 23.
BEGIN failed--compilation aborted at xfw.pl line 23.
Warning: File '/tmp/tp27f0469a_6a2f_48c5_b4fe_03d67e3a3fff' not
found. 
> In mpxfoil at 137
  

And after that I get all the values for alfa, Cl, ..., NaN, so could you help me with some advice about how to solve this issue, and if you can recommend me how to modify the perl wrapper that you build it, so I can get the momentum thickness, separation point, displacement thickness  in matlab.

Thanks a lot in advance,

---

### Post by jeanvaljean53 on 2012-03-13
Hi everyone,
I carrefully read the whole thread. I'm also very interesting in this xfoil/matlab sync for windows. I did all the (neatly explained) adjustement explained in the 8 pages and i eventually get the EXACT same error as you guys:

```
Can't locate IPC/Run.pm in @INC (@INC contains: /usr/lib/perl5/5.10/i686-cygwin /usr/lib/perl5/5.10 /usr/lib/perl5/site_perl/5.10/i686-cygwin /usr/lib/perl5/site_perl/5.10 /usr/lib/perl5/vendor_perl/5.10/i686-cygwin /usr/lib/perl5/vendor_perl/5.10 /usr/lib/perl5/vendor_perl/5.10 /usr/lib/perl5/site_perl/5.8 /usr/lib/perl5/vendor_perl/5.8 .) at xfw.pl line 23.
BEGIN failed--compilation aborted at xfw.pl line 23.
Warning: File
'C:\Users\Ben\AppData\Local\Temp\tp4e2c1cc2_9088_4019_8db7_c05635ce4c3e'
not found. 
> In mpxfoil at 137
  In test at 13
```

If any unix jedi could help go through, i'd be glad.
Cheers

---

### Post by jeanvaljean53 on 2012-03-14
Ok i installed correctly IPC and IO::Pty in the right path through the bash cygwin.
Now i have this error popping out:
```
XFOIL error: Command 'xfoil' not found in /cygdrive/c/Program Files/MATLAB/R2011a/bin/win64, /cygdrive/c/Program Files/Common Files/Microsoft Shared/Windows Live, /cygdrive/c/Program Files (x86)/Common Files/Microsoft Shared/Windows Live, /cygdrive/c/Windows/system32, /cygdrive/c/Windows, /cygdrive/c/Windows/System32/Wbem, /cygdrive/c/Windows/System32/WindowsPowerShell/v1.0, /cygdrive/c/Program Files (x86)/Windows Live/Shared, /cygdrive/c/Program Files/Trend Micro/AMSP, /cygdrive/c/Program Files/Intel/WiFi/bin, /cygdrive/c/Program Files/Common Files/Intel/WirelessCommon, /cygdrive/c/Xfoil/bin, /usr/bin at xfw.pl line 81

Warning: File
'C:\Users\Ben\AppData\Local\Temp\tpdef74a6f_d4e0_4d7e_bd19_5f0ab7d9e344'
not found. 
```It just does not find xfoil somewhere, but i don't know why does it expect it in those weird paths.

---

### Post by pinguinhood on 2012-03-14
I used Matlab to control Ansys Fluent through journal scripts. You can execute shell comand inside Matlab by using ```
unix(xxx)
``` where xxx is the shell comand you want to execute.
For example you can try ```
unix('echo hello world')
```

---

### Post by jeanvaljean53 on 2012-03-14
I realized that my xfoil was not actually installed..
I'm ashamed.
I started now, it's long because i miss a lot a packages like x11. But i think i'll make it.
Maybe then i can directly control Xfoil through system or dos or unix commands i don't know. I'll tell you

---

### Post by azredwing on 2012-03-14
Hi guys - 

I'm glad you all are using my work. Unfortunately I don't really have the time to support it anymore, so this is an official "this code is now unsupported" message.. MPXF did the job for me when I was working in fluids, but I've switched my focus to control theory so I almost never use XFoil anymore. Not to mention I've only done rudamentary tests for compatibility with Windows and none with Mac, so I really have no idea how compatibility will go with those. 

If anyone wants to maintain this, though, PM me. I'll open up the SourceForge or move the project to GitHub if requested.

---

### Post by jeanvaljean53 on 2012-03-15
Hi azredwing,
Thank you for your work and good luck with those Riccati equations.
I have written a Matlab .m function that runs Xfoil on windows without any perl/unix but only the dos command. It uses xfoil 6.96 windows executable. Here is the function code:
```
function[Cl, Cd]=get_coeff(Re,maxit,alfa)

Re=int2str(Re);
maxit=int2str(maxit);
alfa=int2str(alfa);

fopen('coeffs.txt','wt');fclose('all');
fid = fopen('in.txt','wt');
fprintf(fid,'%s','PLOP');fprintf(fid,'\n');
fprintf(fid,'%s','G');fprintf(fid,'\n');
fprintf(fid,'\n');
fprintf(fid,'%s','load NACA0012');fprintf(fid,'\n'); %% load directly my NACA0012 coordinates file.
fprintf(fid,'%s','oper');fprintf(fid,'\n');
fprintf(fid,'%s',['visc ' Re]);fprintf(fid,'\n');
fprintf(fid,'%s',['iter ' maxit]);fprintf(fid,'\n');
fprintf(fid,'%s','pacc');fprintf(fid,'\n');
fprintf(fid,'%s','coeffs.txt');fprintf(fid,'\n');
fprintf(fid,'%s','y');fprintf(fid,'\n');
fprintf(fid,'\n');
fprintf(fid,'%s',['alfa ' alfa]);fprintf(fid,'\n');
fprintf(fid,'%s','pacc');fprintf(fid,'\n');
fprintf(fid,'\n');
fprintf(fid,'%s','quit');
fclose(fid);

dos('xfoil.exe < in.txt');
fid=fopen('coeffs.txt','r');
B=fscanf(fid,'%e');
 if isempty(B)
Cl=0;
Cd=0;
 else
     B=B';
Cl=B(1,2);
Cd=B(1,3);
 end


end

```Note that if Xfoil does not converge, I return Cl=Cd=0.
That's my current issue. I don't understand why it does not converge when i use matlab whereas used manually it does converge for the same set of Re, alpha, maxit.
I didn't include the Mach number but will soon. You can also add the range of alpha argument if you need.
The in.txt command text file used is such:
```
PLOP
G

load NACA0012
oper
visc 248765
iter 100
pacc
coeffs.txt
y

alfa 24
pacc

quit
```It still not very good and it's not ubuntu reliant anymore so just in case some windows people needs it.
Cheers

---

### Post by andross4001 on 2012-09-27
Hi there,
I found the solution of jeanvaljean53 very interesting. I added a minor correction in order to make it work properly (here under linux):

function[Cl, Cd]=get_coeff(Re,maxit,alfa)

Re=int2str(Re);
maxit=int2str(maxit);
alfa=int2str(alfa);

fopen('coeff.txt','wt');
fid = fopen('in.txt','wt');
fprintf(fid,'%s','PLOP');fprintf(fid,'\n');
fprintf(fid,'%s','G');fprintf(fid,'\n');
fprintf(fid,'\n');
fprintf(fid,'%s','NACA0012');fprintf(fid,'\n');
fprintf(fid,'%s','oper');fprintf(fid,'\n');
fprintf(fid,'%s',['visc ' Re]);fprintf(fid,'\n');
fprintf(fid,'%s',['iter ' maxit]);fprintf(fid,'\n');
fprintf(fid,'%s','pacc');fprintf(fid,'\n');
fprintf(fid,'\n');
fprintf(fid,'\n');
fprintf(fid,'%s',['alfa ' alfa]);fprintf(fid,'\n');
fprintf(fid,'%s','pwrt 1');fprintf(fid,'\n');
fprintf(fid,'%s','coeff.txt');fprintf(fid,'\n');
fprintf(fid,'%s','y');fprintf(fid,'\n');
fprintf(fid,'%s','pacc');fprintf(fid,'\n');
fprintf(fid,'\n');
fprintf(fid,'%s','quit');fprintf(fid,'\n');
fclose(fid);

system('xfoil < in.txt');

B=dlmread('coeff.txt','',12,0);
Cl=B(1,2);
Cd=B(1,3);

end


Hope it helps,
regards,
Andreas

---

