---
title: "Quick Checksum Question"
date: 2009-04-23
forum: General Help
---

### Post by DGortze380 on 2009-04-23
Hey All,

Please, I'm trying to finish up this program and can't find what I need.. 

.. I just need a simple utility, for Windows / Ubuntu / OS X, doesn't matter, that will calculate a CHECKSUM.

NOT A HASH. I can't use a HASH. I need a plain old, add the bits, checksum.

---

### Post by codeseer on 2009-04-24
I'm not sure exactly what you're talking about. Take a look at these descriptions and see if one of them is what you want. If it is, then it should be fairly easy to write the code for it.

---

### Post by DGortze380 on 2009-04-24
> **codeseer said:**
> I'm not sure exactly what you're talking about. Take a look at these descriptions and see if one of them is what you want. If it is, then it should be fairly easy to write the code for it.

What descriptions??


I ended up doing it by hand. If anyone knows of a program please post anyways.

To clarify...


A Checksum starts at the first bit of a file and progressing to the last bit, adding 1 for each bit that is on.
A Hash uses a mathematical algorithm to output a hex string based on the bits.

The problem is that I'm searching for Near Matches, not Exact Matches. The hash totally changes if you change 1 bit, where as the checksum only changes by 1.

Example:  10001110101
Checksum: 6
MD5 Hash: 89bb2baf4d384c49ca39f6ed0ffad39


Change it by 1 bit: 10001110100
Checksum: 5
Hash: 44e45c8553418ca2dfabe4e15ebf074e

---

### Post by codeseer on 2009-04-24
I see. :)

---

### Post by paradigm2 on 2009-04-24
> **DGortze380 said:**
> What descriptions??


I ended up doing it by hand. But to clarify...

Checksum: Starting at the first bit of a file and progressing to the last bit, adding 1 for each bit that is on.

Example:  10001110101
Checksum would be: 6

A Hash uses an algorithm to produce a 'code' or 'fingerprint' based on which bits are turned on, but the hash will be entirely different if just 1 bit is different in the file, where as the checksum will only be different by 1 digit.

I'm using it to search for Near Matches to files, not Exact Matches.

Like a CRC check maybe?

I see these packages:

**cfv**

> 
versatile file checksum creator and verifier

cfv is a utility to test and create a wide range of checksum
verification files. It currently supports testing and creating
sfv, sfvmd5, csv, csv2, csv4, md5, bsdmd5, torrent and crc files.
Test-only support is available for par, par2.


**libstring-crc32-perl**

> 

The Digest::CRC module calculates CRC sums of all sorts.
It contains wrapper functions with the correct parameters for CRC-CCITT,
CRC-16 and CRC-32. The module acts similar to libstring-crc32-perl, but
implements the Digest interface.


**libstring-crc-perl**


> 
Perl interface for cyclic redundancy check generation

The CRC32 module calculates CRC sums of 32 bit lengths.
It generates the same CRC values as ZMODEM, PKZIP, PICCHECK and
many others.

Despite its name, this module is able to compute the checksum of
strings as well as of files.


Jacksum

> 
computes checksums, CRCs and message digests

Jacksum is a free and platform independent software for computing and
verifying checksums, CRCs and message digests.  Jacksum features both a
commandline interface and an open API.

Jacksum supports 58 popular algorithms (Adler32, BSD sum, Bzip2's CRC-32,
POSIX cksum, CRC-8, CRC-16, CRC-24, CRC-32 (FCS-32), CRC-64, ELF-32,
eMule/eDonkey, FCS-16, GOST R 34.11-94, HAS-160, HAVAL (3/4/5 passes,
128/160/192/224/256 bits), MD2, MD4, MD5, MPEG-2's CRC-32, RIPEMD-128,
RIPEMD-160, RIPEMD-256, RIPEMD-320, SHA-0, SHA-1, SHA-224, SHA-256,
SHA-384, SHA-512, Tiger-128, Tiger-160, Tiger, Tiger2, Tiger Tree
Hash, Tiger2 Tree Hash, Unix System V sum, sum8, sum16, sum24, sum32,
Whirlpool-0, Whirlpool-1, Whirlpool and xor8).

Some of the additional features include:

 - Fully customizable output
 - Customized CRC algorithms and support for combination of multiple algorithms
 - By default, output is 100% compatible with Unix-standard tools such
   as sum, cksum, md5sum and sha1sum
 - Supports verification of both the content and timestamp of files
 - Large file aware
 - Recursive file processing


Good luck

---

### Post by DGortze380 on 2009-04-24
> **paradigm2 said:**
> Like a CRC check maybe?

I see these packages:

**cfv**



**libstring-crc32-perl**



**libstring-crc-perl**




Jacksum



Good luck

thanks for the info, I'll start going through it.

---

### Post by paradigm2 on 2009-04-24
Hmmm.  Apparently also do 'man cksum' ?

---

