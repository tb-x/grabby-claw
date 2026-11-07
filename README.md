# Grabby Claw

A 3D claw machine game for young kids (around age 5), made for phones and tablets. The glass box is full of plush toys: put in a coin, steer the claw over a toy, press the big red button and see if it holds on all the way to the prize hole.

- **Tap the gold coin** and it rolls into the coin slot, the lights flash and the claw wakes up. Coins never run out.
- **Steer the claw** with the joystick, or just tap the toy you want (or drag a finger on the machine) and the claw slides over it. A yellow ring shines on whatever is right under the claw, and turns green when a toy is in reach. That toy bounces a little, saying "pick me!".
- **Press the big red button** and the claw opens, drops down until it lands on a toy (or the floor), closes and lifts. Then it carries what it caught over to the hole in the front-left corner and lets go.
- **Twelve toys to collect**: a teddy bear, bunny, duck, frog, piggy, panda, penguin, kitty, ladybird, octopus, unicorn and dinosaur, all built in code from simple shapes.
- **A prize** drops through the hole, pops out of the prize door and shows big in the middle of the screen with light rays, confetti and a fanfare, and the device's voice says what it is. A tap (or waiting a moment) sends it hopping onto the shelf.
- **The shelf** (top right, with the teddy and a number) shows every toy: ones found so far in colour with how many, the rest as shadows. Tap a toy on the shelf and it wiggles and says its name. It's remembered on the device.
- **Gentle on misses.** Nothing is ever lost. A toy caught near its edge, or under other toys, may wriggle free on the way up or across ("Whoops!"), and an empty claw gets a friendly "Try again!". After two tries without a prize, the next toy the claw closes on is held for sure. A toy that wriggles free near the hole, or gets bumped over the hole's low wall, can fall in by luck: that counts too.
- **The machine refills** itself when it's getting empty, with toys not yet on the shelf more likely to drop in.
- **Toys behave like soft balls**: they pile up, tumble when dropped, roll a little and settle back upright facing you.
- **Sound** is all made in the browser: a bouncy arcade tune, the motor hum, the coin clink, claw clacks, a squeak when a toy is caught, the fanfare. Spoken lines (what to do the first few times, the prize's name) use the device's own voice.

🏠 in the top-left corner goes back to the list of all games, and the speaker in the top-right corner turns sound off and on. On a computer, the arrow keys (or WASD) steer and Space puts in a coin and grabs.

## Run it

It's one page. Serve the folder (for example `python -m http.server 5238`) and open it in a browser. It needs an internet connection the first time, for three.js and the font. No build step. Opening `index.html` straight from disk works too.

## Play offline (add to Home Screen)

On iPhone or iPad, open the game in Safari, tap **Share → Add to Home Screen**, then open it once from the new icon while online. After that it starts full screen and works without internet. Changes arrive on their own: the launch that downloads them shows them.

(How: `manifest.webmanifest` gives the icon and full-screen mode; `sw.js`, a service worker, keeps a copy of every file the game uses. The icons `icon-180.png` and `icon-512.png` are rendered from `icon.svg` in headless Chrome.)

## Tuning knobs

At the top of the script in `index.html`:

- `MOVE_SPEED`, `DROP_SPEED`, `LIFT_SPEED`, `CARRY_SPEED`: how fast the claw slides, drops, lifts and carries (the box is 4.2 units wide).
- `HOLD_CENTRE`, `HOLD_EDGE`: the chance a caught toy stays held all the way to the hole, for one caught right in the middle and one only just caught by its edge.
- `GRAB_REACH`: how far off-centre still catches a toy, in toy sizes.
- `BURIED`: the hold chance is multiplied by this for each toy lying on top of the one caught.
- `LUCKY_AFTER`: after this many tries in a row with no prize, the next toy caught is held for sure.
- `TOYS_IN`, `REFILL_AT`: toys in a full machine, and how few are left before a fresh load drops in.
- `NEW_TOY_PULL`: how much likelier a toy not yet on the shelf is to go into the machine.
- `GRAVITY`: how floaty the toys fall.
- `HELP_TIMES`: how many times ever the how-to lines are spoken.
- `IDLE_HINT`: seconds of nothing before the coin, joystick or button nudges.
- `PRIZE_SHOW`: seconds a prize is shown before it hops onto the shelf by itself.
- `MUSIC_VOL`, `MUSIC_BPM`: the arcade tune's volume and speed.
