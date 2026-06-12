---
title: "Contents of file with extension .theme are replaced when renaming"
date: 2008-10-02
forum: Desktop Environments
---

### Post by Blueapples on 2008-10-02
I'm using Ubuntu 8.04, and doing some file work using Nautilus 2.22.3. to be honest, I have no idea if this is an Ubuntu, Gnome, or Nautilus issue.

The screen shots attached show... a very strange thing happening. I found this while working with Drupal theme files. If I rename a file that already has the .theme extension, it's contents are suddenly replaced. With this:

```

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=art.theme
Name[en_US]=art.theme

['language']
$direction = $GLOBALS['language']->direction ? 'rtl' : 'ltr';
drupal_set_html_head('<link rel="shortcut icon" href="'. check_url(theme_get_setting('favicon')) .'" type="image/x-icon" />');
$title = drupal_get_title();
$blocks_top = theme_blocks('top');
$blocks_left = theme_blocks('left');
$blocks_right = theme_blocks('right');
$output  = "<div class=\\"comment". ' '. $status ."\\">\n";
$output .= "</div>\n";
if ($logo = theme_get_setting('logo')) {
$primary_links = theme('links', menu_primary_links(), array('class' => 'links', 'id' => 'navlist'));
$secondary_links = theme('links', menu_secondary_links(), array('class' => 'links', 'id' => 'subnavlist'));
if ($tabs = theme('menu_local_tasks')) {
if ($footer = variable_get('site_footer', '')) {
function chameleon_node($node, $teaser = 0, $page = 0) {
$submitted['node_submitted'] = theme_get_setting("toggle_node_info_$node->type") ? array(
'title' => t('By !author at @date', array('!author' => theme('username', $comment), '@date' => format_date($comment->timestamp, 'small'))),
'html' => TRUE);
$terms = taxonomy_link("taxonomy terms", $node);
$links = array_merge($links, $node->links);
function chameleon_comment($comment, $node, $links = array()) {
$submitted['comment_submitted'] = array(
if ($help = menu_get_active_help()) {
return '<div class="help">'. $help .'</div><hr />';

```

This is a real example of what happened when I tried to rename a .theme file. That is the whole file that remains. The version of the file that's on the server (thank God - this has a lot of customizations in it) is a few hundred lines long.

This doesn't happen when adding the .theme extension to a file that doesn't already have it.

The screen shots attached show me creating a new file, renaming it to test.theme, then renaming it to test2.theme, where suddenly it is populated with this INI formatted data.

Here's a shell session right after doing this:

```

isaac@isaac-laptop:~/test$ cat test2.theme
cat: test2.theme: No such file or directory
isaac@isaac-laptop:~/test$ ls
test.theme
isaac@isaac-laptop:~/test$ ls ./test.theme
./test.theme
isaac@isaac-laptop:~/test$ cat ./test.theme
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=test2.theme
Name[en_US]=test2.theme

```

That's right, the test2.theme file **does not exist**. But the contents of test.theme are the same weird INI data that I see in the Nautilus icon preview as being in test2.theme.

The last screen shot [UbuntuThemeFiles-after.png]("http://ubuntuforums.org/attachment.php?attachmentid=87104&stc=1&d=1223001328") shows the state of the Nautilus view a few minutes after doing this - refreshed, along side the output of ls. Both are clearly in the same directory. Both clearly show different file names.

So...

WTF is going on here?

---

