---
title: "gscan2pdf error in Ubuntu 8.04"
date: 2009-01-31
forum: General Help
---

### Post by DDBrewer on 2009-01-31
I'm running Ubuntu 8.04 and trying to scan documents to djvu format with gscan2pdf and an HP 3970 scanner.  When I try to run a scan with gscan2pdf, from the GUI or the terminal, I get the following error: "Unknown message: scanimage: sane_start: Invalid argument".  I've searched the forums and the web generally, and can't find anything that seems to give a fix for my problem. 

Here's the output from gscan2pdf --debug:


$ gscan2pdf --debug
gscan2pdf 0.9.21
Using en_US.UTF-8 locale
Gtk2-Perl version 1.161
Built for 2.12.0
Running with 2.12.9
$VAR1 = {
          'ocr panel' => '625',
          'frontend' => 'scanimage',
          'mode' => 'Gray',
          'Paper' => {
                       'US Legal' => {
                                       'l' => '0',
                                       'y' => '356',
                                       'x' => '216',
                                       't' => '0'
                                     },
                       'US Letter' => {
                                        'l' => '0',
                                        'y' => '279',
                                        'x' => '216',
                                        't' => '0'
                                      },
                       'A4' => {
                                 'l' => '0',
                                 'y' => '297',
                                 'x' => '210',
                                 't' => '0'
                               }
                     },
          'window_maximize' => '1',
          'white-threshold' => '0.9',
          'y' => '0',
          'layout' => 'single',
          'cwd' => '/home/isr',
          't' => '0',
          'OCR on scan' => '',
          'Paper size' => 'Manual',
          'Page range' => 'all',
          'window_height' => '801',
          'startup warning' => '',
          'pages to scan' => '1',
          'resolution' => '300',
          'unpaper on scan' => '',
          'source' => 'Flatbed',
          'x' => '0',
          'downsample dpi' => '150',
          'window_width' => '1440',
          'threshold tool' => '80',
          'window_x' => '0',
          'deskew-scan-direction' => 'left,right',
          'window_y' => '46',
          'thumb panel' => '181',
          'enable options' => '1',
          'version' => '0.9.21',
          'device' => 'hp3900:libusb:006:005',
          'l' => '0',
          'Page range default' => 'all',
          'downsample' => '',
          'black-threshold' => '0.33',
          'restore window' => '1'
        };
Found PDF::API2
Found Image::Magick
Found ImageMagick
Found xdg-email
Found cjb2 (djvu)
Found libtiff
scanimage --formatted-device-list="'%i','%d','%v %m'
" 2>/dev/null
Forked PID 6586
Waiting to reap process at /usr/bin/gscan2pdf line 3523.
Reaped PID -1
'0','hp3900:libusb:006:005','Hewlett-Packard Scanjet 3970'
scanimage --help --device-name='hp3900:libusb:006:005' --mode='Gray'
Forked PID 6594
Waiting to reap process at /usr/bin/gscan2pdf line 4443.
Reaped PID -1
Usage: scanimage [OPTION]...

Start image acquisition on a scanner device and write PNM image data to
standard output.

Parameters are separated by a blank from single-character options (e.g.
-d epson) and by a "=" from multi-character options (e.g. --device-name=epson).
-d, --device-name=DEVICE   use a given scanner device (e.g. hp:/dev/scanner)
    --format=pnm|tiff      file format of output file
-i, --icc-profile=PROFILE  include this ICC profile into TIFF file
-L, --list-devices         show available scanner devices
-f, --formatted-device-list=FORMAT similar to -L, but the FORMAT of the output
                           can be specified: %d (device name), %v (vendor),
                           %m (model), %t (type), and %i (index number)
-b, --batch[=FORMAT]       working in batch mode, FORMAT is `out%d.pnm' or
                           `out%d.tif' by default depending on --format
    --batch-start=#        page number to start naming files with
    --batch-count=#        how many pages to scan in batch mode
    --batch-increment=#    increase number in filename by an amount of #
    --batch-double         increment page number by two for 2sided originals
                           being scanned in a single sided scanner
    --batch-prompt         ask for pressing a key before scanning a page
    --accept-md5-only      only accept authorization requests using md5
-p, --progress             print progress messages
-n, --dont-scan            only set options, don't actually scan
-T, --test                 test backend thoroughly
-h, --help                 display this help message and exit
-v, --verbose              give even more status messages
-B, --buffer-size          change default input buffersize
-V, --version              print version information

Options specific to device `hp3900:libusb:006:005':
  Geometry:
    -l 0..220mm (in steps of 1) [220]
        Top-left x position of scan area.
    -t 0..300mm (in steps of 1) [300]
        Top-left y position of scan area.
    -x 0..0mm (in steps of 1) [0]
        Width of scan-area.
    -y 0..0mm (in steps of 1) [0]
        Height of scan-area.
    --resolution 50|75|100|150|200|300|600|1200|2400dpi [50]
        Sets the resolution of the scanned image.
    --red-gamma-table 0..65535,...
        Gamma-correction table for the red band.
    --green-gamma-table 0..65535,...
        Gamma-correction table for the green band.
    --blue-gamma-table 0..65535,...
        Gamma-correction table for the blue band.
    --source Flatbed|Slide|Negative [Flatbed]
        Selects the scan source (such as a document-feeder).
    --mode Color|Gray|Lineart [Gray]
        Selects the scan mode (e.g., lineart, monochrome, or color).
    --depth 8|16bit [8]
        Number of bits per sample, typical values are 1 for "line-art" and 8
        for multibit scans.
    --threshold 0..255 [inactive]
        Select minimum-brightness to get a white point
  Debugging Options:
    --opt_model HP3800|HP3970|HP4070|HP4370|UA4900|HPG3010|BQ5550 [HP3800]
        Allows to test device behaviour with other supported models
    --opt_negative[=(yes|no)] [no]
        Image colours will be inverted
    --opt_nogamma[=(yes|no)] [no]
        Gamma correction will be disabled
    --opt_nowshading[=(yes|no)] [no]
        White shading correction will be disabled
    --opt_realdepth[=(yes|no)] [no]
        If gamma is enabled, scans are always made in 16 bits depth to improve
        image quality and then converted to the selected depth. This option
        avoids depth emulation.
    --opt_emulategray[=(yes|no)] [no]
        If enabled, image will be scanned in color mode and then converted to
        grayscale by software. This may improve image quality in some
        circumstances.
    --opt_nowarmup[=(yes|no)] [no]
        Warmup process will be disabled
    --opt_dbgimages[=(yes|no)] [no]
        If enabled, some images involved in scanner processing are saved to
        analyze them.
    --opt_reset
        Resets chipset data
  Information:
    --opt_infoupdate
        Updates information about device
  Buttons:

Type ``scanimage --help -d DEVICE'' to get list of all options for DEVICE.

List of available devices:
    hp3900:libusb:006:005
$VAR1 = {
          'source' => {
                        'tip' => 'Selects the scan source (such as a document-feeder).',
                        'default' => 'Flatbed',
                        'values' => [
                                      'Flatbed',
                                      'Slide',
                                      'Negative'
                                    ]
                      },
          'opt_nowshading' => {
                                'tip' => 'White shading correction will be disabled',
                                'default' => 'no',
                                'values' => [
                                              'yes',
                                              'no'
                                            ]
                              },
          'opt_negative' => {
                              'tip' => 'Image colours will be inverted',
                              'default' => 'no',
                              'values' => [
                                            'yes',
                                            'no'
                                          ]
                            },
          'threshold' => {
                           'tip' => 'Select minimum-brightness to get a white point',
                           'min' => '0',
                           'max' => '255',
                           'default' => 'inactive'
                         },
          'mode' => {
                      'tip' => 'Selects the scan mode (e.g., lineart, monochrome, or color).',
                      'default' => 'Gray',
                      'values' => [
                                    'Color',
                                    'Gray',
                                    'Lineart'
                                  ]
                    },
          'opt_nogamma' => {
                             'tip' => 'Gamma correction will be disabled',
                             'default' => 'no',
                             'values' => [
                                           'yes',
                                           'no'
                                         ]
                           },
          'depth' => {
                       'tip' => 'Number of bits per sample, typical values are 1 for "line-art" and 8 for multibit scans.',
                       'default' => '8',
                       'values' => [
                                     '8',
                                     '16bit'
                                   ]
                     },
          'opt_nowarmup' => {
                              'tip' => 'Warmup process will be disabled',
                              'default' => 'no',
                              'values' => [
                                            'yes',
                                            'no'
                                          ]
                            },
          'opt_realdepth' => {
                               'tip' => 'If gamma is enabled, scans are always made in 16 bits depth to improve image quality and then converted to the selected depth. This option avoids depth emulation.',
                               'default' => 'no',
                               'values' => [
                                             'yes',
                                             'no'
                                           ]
                             },
          'resolution' => {
                            'tip' => 'Sets the resolution of the scanned image.',
                            'default' => '50',
                            'values' => [
                                          '50',
                                          '75',
                                          '100',
                                          '150',
                                          '200',
                                          '300',
                                          '600',
                                          '1200',
                                          '2400dpi'
                                        ]
                          },
          'opt_emulategray' => {
                                 'tip' => 'If enabled, image will be scanned in color mode and then converted to grayscale by software. This may improve image quality in some circumstances.',
                                 'default' => 'no',
                                 'values' => [
                                               'yes',
                                               'no'
                                             ]
                               },
          'opt_model' => {
                           'tip' => 'Allows to test device behaviour with other supported models',
                           'default' => 'HP3800',
                           'values' => [
                                         'HP3800',
                                         'HP3970',
                                         'HP4070',
                                         'HP4370',
                                         'UA4900',
                                         'HPG3010',
                                         'BQ5550'
                                       ]
                         },
          'opt_dbgimages' => {
                               'tip' => 'If enabled, some images involved in scanner processing are saved to analyze them.',
                               'default' => 'no',
                               'values' => [
                                             'yes',
                                             'no'
                                           ]
                             }
        };
$VAR1 = [];
$VAR1 = {
          'l' => '0',
          'y' => '0',
          'source' => 'Flatbed',
          'mode' => 'Gray',
          'resolution' => '300',
          'x' => '0',
          't' => '0'
        };
scanimage --device-name='hp3900:libusb:006:005' --mode='Gray' -l 0 -y 0 --source='Flatbed' --resolution='300' -x 0 -t 0 --batch --progress --batch-count=1
Forked PID 6608
Scanning 1 pages, incrementing by 1, numbering from 1
Scanning page 1
scanimage: sane_start: Invalid argument
Waiting to reap process at /usr/bin/gscan2pdf line 3860.
Reaped PID 6608


I would be very grateful for any tips how to make gscan2pdf functional with my set-up.  

Thank you!

- Devon

---

### Post by lykwydchykyn on 2009-01-31
My last scanner was a 3970; unfortunately it is now a doorstop after my kids knocked it off the desk one too many times, so I'm going purely by memory here.  I tried many times to get gscan2pdf going; seems like I ultimately figured out that it was not setting the paper size correctly so xsane was erroring out.

Note this line in your debug output:
```

scanimage --device-name='hp3900:libusb:006:005' --mode='Gray' -l 0 -y 0 --source='Flatbed' --resolution='300' -x 0 -t 0 --batch --progress --batch-count=1

```

it says "-l 0 -y 0 -x 0 -t 0" -- this means there is no width or height to the scan area.

I believe if you manually set these it will scan, but I never found a way to have it do this in any kind of automatic way or to keep the settings between scans.

I've replaced the scanner now and my new scanner works with it flawlessly, so it's something peculiar to the hp 3900 series.

---

### Post by DDBrewer on 2009-01-31
Thank you for your advice, lykwydchykyn.  

I think you have diagnosed my problem right on the nose.  I tried to change the paper size, but I get some strange responses from gscan2pdf.  If paper size is set as "manual" then I can only modify "left" and "top"; when I try to edit "width" and "height", whatever value I enter automatically resets to 0.  If I try to change the paper size to "edit", it rejects the default options (US letter, US legal, A4) or any new dimensions that I add.  

I can scan with the width and height settings at 0 as long as left and top values are greater than 0, but then all I get are variations of gray (no matter what the values are ranging from 1 to 200 or what the mode is or what the resolution is), even though the document page I'm scanning is filled with text.  

What further ideas do you have?

Thank you for your help!

- Devon

---

### Post by lykwydchykyn on 2009-01-31
Honestly I don't know that there's much you can do; gscan2pdf is a perl script, and if memory serves I may have gone through it and pulled out the width & height specifications (scanimage will just default to the whole scanning area without the, IIRC).  But grepping through the file now I can't remember where I did that.  I don't know PERL so it was mostly guesswork.

I would report this as a bug and use some other program to scan until they can get this fixed.

---

### Post by DDBrewer on 2009-01-31
Thank you for your follow-up.  I've just reported it as a bug at the gscan2pdf SourceForge site.  

- Devon

---

### Post by shawmutt on 2009-03-06
Well, I've been searching around for an answer to this as well.  I may not be able to program, but I can find a workaround to just about anything.  My method may or may not help for you.

I use three workspaces.  The first workspace is for xsane.  I open up the multipage project, and direct it to scan to my desktop, /home/name/desktop.  I'm able to preview, and each page I scan gets saved as a file on the desktop.

After I scan all my pages, I switch to my second workspace, where I have Gimp booted up.  I right click on one of the pics, open with Gimp, and from the toolbar use Image>Mode>Indexed, to chop it down to a 1 bit for text documents, or 16 bit for color.  I save and close that page, and continue until all the pages are done.

I save the files, and move to my third workspace, where I have gscan2pdf running.  I simply import the scanned and corrected images from my desktop, save it, and voila! a multipage document in a reasonable sized PDF.  I hit the "clear all pages" button on gscan2pdf, hit the "create project" and then "delete project" buttons on my xsane, and I'm ready for the next set of documents.

Typing it out makes it sound more complicated than it is, I've got it down to a science now, praise be to workspaces!  Now if I knew some programming, I could probably build something to do all that ;)

---

