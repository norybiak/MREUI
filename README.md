# MREUI

## Install
Download source

Then `npm install`

Copy / paste the iconPacks into your public folder. This library comes with a basic pack for creating media player UI. This library assumes the pack folder contains `icons.png` and `planes.glb`. Custom names for these assets is not yet available.

## Basic Usage

```typescript

const UI = new MREUI.UI(this.context, {
	scale: 1
});

await this.UI.loadIconPack(`${this.baseUrl}/iconPacks/media`);

const group = this.UI.createGroup('rootGroup');

const icon = group.createIcon(MREUI.MediaIcons.Play, {
	name: "playBtn",
	position: { x: 1 }
}).addBehavior('released', () => play())

const label = this.mediaContainer.createLabel('Play', {
	position: { x: 1, y: 1 }
});


```

## API

### `UI.createGroup(name: string, options?)`
#### Returns a new Group object
#### Options
```
// Set a group scale for all child elements
groupScale: number
```

### `Group.createIcon(icon: string, options?)`
#### Returns a new Icon object
#### Methods
```
Icon.addBehavior(action: string, actionHandler: () => {})

actions:

pressed
holding
released
enter
hovering
exit
click
```

### `Group.createLabel(text: string, options?)`
#### Returns a new Label object
#### Methods
```
set(content: string) // Changes the text of the label
clear() // Removes the text
```


### Shared options for Icon and Label

```
name?: string
position?: Partial<MRE.Vector3Like>
scale?: MRE.Vector3Like
rotation?: MRE.Quaternion
height?: number
anchor?: MRE.TextAnchorLocation
justify?: MRE.TextJustify
color?: MRE.Color3
enabled?: boolean
mask?: MRE.GroupMask
material?: MRE.Material
parentId?: MRE.Guid
actor?: Partial<MRE.ActorLike> // note, specifying actor options will override any of the above
```

### Shared methods for Icon and Label
```
show() //Shows the element
hide() //hides the element
toggleVisibility() //Flips the visibility state
enableCollider() //Enables the collider
disableCollider() //disables the collider 
toggleCollider() //flips the current state of the collider
```
