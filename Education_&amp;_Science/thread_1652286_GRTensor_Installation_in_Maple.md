---
title: "GRTensor Installation in Maple"
date: 2010-12-24
forum: Education &amp; Science
---

### Post by timtaves on 2010-12-24
Hey there, I just installed Maple 13 and I can't figure out how to add the GRTensor package.  I downloaded the Unix version (there isn't a specific Linux version) and followed the instructions that came with it.  The last step says to copy a file into the .mapleinit file (which doesn't exist) in the home folder.  Any ideas?

Thanks, Tim

---

### Post by dsfitzpat on 2010-12-26
Hey Tim,
I haven't tried running Maple before but it's possible Maple doesn't generate its config files in the home folder until after you've run it once - I'd say run the program, then close it.
Then go to your home folder, and hit Ctrl-H (since .anything is a hidden file/folder) and see if the missing file is there.  ("copy a file into the .mapleinit" sounds as though .mapleinit might be a folder rather than a file - unless it's a plain text file and you're copying and pasting the contents of the GR tensor macros into it.)

---

### Post by timtaves on 2010-12-26
I actually already had opened and closed Maple before trying to install GRTensor.  Thanks for the attempt though.

As for the .mapleinit file/folder, I think that this is in the Unix and possibly even in Macs operating system but not in Linux.  There must be some equivalent folder though.

---

### Post by ianhoolihan on 2011-03-21
Sorry to restart this thread, but was this issue resolved? I too cannot find the mapleinit file in my home directory, however I have found one called mapleinit.m, which contains the following:

> function mapleinit(force)
% mapleinit - initialize Maple session
%
% Description: 
%
% The mapleinit script runs automatically at the beginning of a Maple
% session.  A Maple session is started whenever a command uses Maple
% to compute something.  It is not intended that this script be called 
% directly by the user.
%
% The mapleinit script usually contains commands that help make Maple
% more like MATLAB.  For example the alias pi=Pi is set so that string
% expressions used by the MAPLE command will accept pi = 3.14... 
%
% For a complete list of commands executed during the initialization of
% Maple, see the file <code>$matlabroot/toolbox/maple/mapleinit.m</code>.
%
% These commands will also affect the behavior of the Maple GUI launched
% via the command MAPLE, but not all user-added interface settings
% will immediately apply after using Maple's RESTART command.  A
% computation must be invoked on the MATLAB side before mapleinit.m is
% read.
%
% See Also:
%    maple
%
% 
% Copyright (c) Maplesoft, a division of Waterloo Maple Inc. 2007
% All rights reserved. Maple is a trademark of Waterloo Maple Inc.
if nargin ~= 1 || ~islogical(force) || ~force
    error('Not intended to be called directly');
end

try
    maple('interface(''prettyprint''=1,''imaginaryunit''='':-` i`''):');
    maple(':-i := ` i`:');
    maple(':-j := ` i`:');
    maple(':-I := ` i`:');
    maple('alias(dirac=Dirac,heaviside=Heaviside,pi=Pi,acos=arccos,acosh=arccosh):');
    maple('alias(acot=arccot,acoth=arccoth,acsc=arccsc,acsch=arccsch,asec=arcsec):');
    maple('alias(asech=arcsech,asin=arcsin,asinh=arcsinh,atan=arctan,atanh=arctanh):');
    maple('alias(besseli=BesselI,besselj=BesselJ,besselk=BesselK,bessely=BesselY):');
    maple('alias(cosint=Ci,fix=trunc,gamma=GAMMA,imag=Im,iztrans=invztrans):');
    maple('alias(lambertw=LambertW,real=Re,sinint=Si,zeta=Zeta,conj=conjugate):');
    maple('alias(eulergamma=gamma):');
    maple('alias(log=ln):');
    maple('addproperty(''unreal'',{},{}):');
    maple('interface(showassumed=0):');
    maple('interface(plotdevice=inline)');
    maple('inf := infinity:');
    maple('nan := undefined:');
    maple('Inf := infinity:');
    maple('NaN := undefined:');
    maple('_EnvUseClientJVM := false');
catch
    error(lasterror);
endDoes anyone know if this if the correct file? If so, where would I paste the contents of the mapleinit.sample file?

Thanks

---

### Post by mansourk on 2011-03-27
Hi,
I have installed GRTensor for unix in Maple 13 succesfully. in my case also there was not a ".mapleinit" file in the home folder so i made a document there  with the name ".mapleinit" and simply copied the  contents of  "mapleinit.sample"  file to it. in my case it worked and i hope it could help you.

---

