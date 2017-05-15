Slope Calc
==========

## Example

Scss Input:
```scss
.my-widget {
  @include slope-calc(padding, 20px 320px, 60px 1440px);
}
```

CSS Result:
```css
.my-widget {
  padding: calc(3.57143vw + .53571rem);
}
```

## Usage

The first argument is a single property or a list of properties (space separated).

The following arguments are lists containing 2 numbers. The first item is the target value.
The second item is the screen width that the property should equal the first value.

## Flags
Flags are an optional argument passed in as the last argument.
In scss, strings work with or without quotes.

- `important`
  apply the css "!important" flag to the property (or properties) at all breakpoints.
  
  Scss Input:
  ```scss
  .my-widget {
    @include slope-calc(padding, 20px 320px, 60px 1440px, 60px 1441px, important);
  }
  ```
  
  CSS Result:
  ```css
  .my-widget {
    padding: calc(3.57143vw + .53571rem) !important;
  }
  
  @media only screen and (min-width: 90em) {
    .my-widget {
      padding: 3.75rem !important;
    }
  }
  ```

- `clip`
  add a media query at the largest breakpoint that sets the property to a fixed value
  
  Scss Input:
  ```scss
  .my-widget {
    @include slope-calc(padding, 20px 320px, 60px 1440px, clip);
  }
  ```
  
  CSS Result:
  ```css
  .my-widget {
    padding: calc(3.57143vw + .53571rem);
  }
  
  @media only screen and (min-width: 90em) {
    .my-widget {
      padding: 3.75rem;
    }
  }
  ```
  
## More Examples

Scss Input:
```scss
.my-widget {
  @include slope-calc(margin padding, 20px 320px, 60px 1440px, clip);
}
```

CSS Result:
```css
.my-widget {
  margin: calc(3.57143vw + .53571rem);
  padding: calc(3.57143vw + .53571rem);
}

@media only screen and (min-width: 90em) {
  .my-widget {
    margin: 3.75rem;
  }
}
@media only screen and (min-width: 90em) {
  .my-widget {
    padding: 3.75rem;
  }
}
```

## Browser Support
- IE 9+
- Chrome 19+
- Firefox 4+
- Safari 6+
- Android 4.4+
