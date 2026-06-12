---
title: "How to get Firefox the same when run as user or root/ KDE-Kubuntu"
date: 2009-01-22
forum: Desktop Environments
---

### Post by Bob Distler on 2009-01-22
Was also posted in Kubuntu's forum
My question is:
**Why** when I run Firefox as 'user' selected highlighting **WILL NOT** work?
**but** when I run Firefox (same file) as 'Root' selected highlighting **WILL** work?

This project is for a "Community Food/Clothing Bank"
with 11 units in a network using WinXP/Firefox - if I can get this
highlighting fixed I can move all 11 to KDE-Kubuntu/Firefox.

I have made a test Web page, from one of the check-out-desks pages
with 3 HTML '...<select><option>...' as columns
when you click on a 'option' it is highlighted BUT it
will NOT stay highlighted when you click a 'option' in one of the
other columns or outside of the columns when you run:

usr/lib/firefox-3.0.5/firefox as 'user'.

When you run the same file as 'Root' all selected options stay highlighted.
(Note: Firefox's 'skin' is not the same when run as 'user' or 'Root')

I am new to KDE-Kubuntu and I think something in the setup needs to changed
but what and where I do not know, and that is what I need help with.

Here is data I have that looks to me - it is the same as 'user' or 'Root'
Run as 'user' Firefox Help/About shows:
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.5)
Gecko/2008121621 Ubuntu/8.04 (hardy) Firefox/3.0.5

Run as 'root' Firefox Help/About shows:
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.5)
Gecko/2008121621 Ubuntu/8.04 (hardy) Firefox/3.0.5

Run as 'user' Web site  shows:
[HTTP_USER_AGENT] => Mozilla/5.0 (X11; U; Linux i686;
en-US; rv:1.9.0.5) Gecko/2008121621 Ubuntu/8.04 (hardy) Firefox/3.0.5

Run as 'root' Web site shows:
[HTTP_USER_AGENT] => Mozilla/5.0 (X11; U; Linux i686;
en-US; rv:1.9.0.5) Gecko/2008121621 Ubuntu/8.04 (hardy) Firefox/3.0.5

From 'log' file:
[    0.000000] Linux version 2.6.24-22-generic (buildd@vernadsky)
 (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7))
 #1 SMP Mon Nov 24 18:32:42 UTC 2008 (Ubuntu 2.6.24-22.45-generic)

From Help - About
KDE 3.5.10
K Desktop environment 3.5.10

Here is a test Web site and the code used on it

URL for online test
[http://www.bobdistler.com/ccs_test/test_select.html](http://www.bobdistler.com/ccs_test/test_select.html)

Code used on test page 'test_select.html'.```

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
  <head>
    <meta http-equiv="content-type" content="text/html; charset=ISO-8859-1">

    <title>
      Test Firefox select-option-highlighted
    </title>
  </head>
<body>

<form id="postForm" name="postForm" action="" method="get">
  <table id="tSelect" name="tSelect">
    <tbody>
      <tr>
        <td>
          <select name="tCatalog" size="17">
            <option selected="yes"> Select </option>
            <option>Adult</option>
            <option>Boy</option>
            <option>Boy Infant</option>
            <option>Boy Toddler</option>
            <option>Child</option>
            <option>Girl</option>
            <option>Girl Infant</option>
            <option>Girl Juniors</option>
            <option>Girl Teenager</option>
            <option>Girl Toddler</option>
            <option>Household</option>
            <option>Male Teenager</option>
            <option>Mens</option>
            <option>Misses</option>
            <option>N/A</option>
            <option>Womens</option>
          </select>
        </td>

        <td>
          <select name="tItem" size="43">
            <option selected="yes"> Select </option>
            <option>Accessory</option>
            <option>Adult Pampers</option>
            <option>baby pampers</option>
            <option>Belt</option>
            <option>Blanket</option>
            <option>Bra</option>
            <option>Coat</option>
            <option>Dress or Skirt</option>
            <option>Gloves</option>
            <option>Hankiy</option>
            <option>hat</option>
            <option>Jacket</option>
            <option>Jean Shorts</option>
            <option>Jeans</option>
            <option>Nylons or Tights</option>
            <option>Onesies</option>
            <option>Pads</option>
            <option>Panti liners</option>
            <option>Pants</option>
            <option>Pillow</option>
            <option>PJ</option>
            <option>purses</option>
            <option>Robe</option>
            <option>Scarf</option>
            <option>Sheetset</option>
            <option>shirt</option>
            <option>Shoes</option>
            <option>Shorts</option>
            <option>Sleeper</option>
            <option>Slip</option>
            <option>slippers</option>
            <option>Socks</option>
            <option>Suit</option>
            <option>Sweaters</option>
            <option>Tampons</option>
            <option>Tie</option>
            <option>Tops</option>
            <option>towels</option>
            <option>Undershirt</option>
            <option>Underwear</option>
            <option>Vest</option>
            <option>Wipes</option>
          </select>
        </td>

        <td>
          <select name="tQty" size="11">
            <option selected="yes">0</option>
            <option>1</option>
            <option>2</option>
            <option>3</option>
            <option>4</option>
            <option>5</option>
            <option>6</option>
            <option>7</option>
            <option>8</option>
            <option>9</option>
            <option>10</option>
          </select>
        </td>
      </tr>
    </tbody>
  </table>
</form>
</body>
</html>

```

---

