### preact
---
https://github.com/developit/preact

```js
import { h, render } from 'preact';
render((
  <div id="foo">
    <span>Hello</span>
    <button onClick={ e => alert("hi") }>Click</button>
  </div>
), document.body);

import { h, render, Component } from 'preact';
class Clock extends Component {
  render(){
    let time = new Date();
    return <time datetime={time.toISOString()}>{ time.toLocaleTimeString() }</time>;
  }
}
render(<Clock />, document.body);

import { h, render, Component } from 'preact';
class Clock extends Component {
  constructor(){
    super();
    this.state = {
      time: Date.now()
    };
  }
  componentDidMount(){
    this.timer = setInterval(() => {
      this.setState({ time: Date.now() });
    }, 1000);
  }
  componentWillUnmount(){
    clearInterval(this.timer);
  }
  render(props, state){
    let time = new Date(state.time).toLocaleTimeString();
    return <span>{ time }</span>;
  }
}
render(<Clock />, document.body);

class Foo extends Component {
  @bind
  updateText(e){
    this.setState({ text: e.target.value });
  }
  render({ }, { text }){
    return <input value={text} onInput={this.updateText} />;
  }
}

import linkState from 'linkstate';
class Foo extends Component{
  render({ }, { text }){
    return <input value={text} onInput={linkState(this, 'text')} />;
  }
}

class Link extends Component{
  render(props, state){
    return <a href={props.href}>{props.children}</a>;
  }
}

class Link extends Component {
  render({ href, children }){
    return <a {...{href, children }} />;
  }
}

class Link extends Component {
  render(props){
    return <a {...props} />;
  }
}
const Link = ({ children, ...props }) => (
  <a {...props}>{ children }</a>
);

class BoundComponent extends Component {
  constructor(props){
    super(props);
    this.bind();
  }
  bind(){
    this.binds = {};
    for(let i in this){
      this.binds[i] = this[i].bind(this);
    }
  }
}
class Link extends BoundComponent {
  click(){
    open(this.href);
  }
  render(){
    let { click } = this.binds;
    return <span onClick={ click }>{ children }</span>;
  }
}

class MixedCompnent extends Component {
  constructor(){
    super();
    (this.mixins || []).forEach( m => Object.assign(this, m) );
  }
}

import { h, Component, render } from 'preact';
require('preact/debug');

new webpack.DefinePlugin({
  'process.env': {
    'NODE_ENV': JSON.stringify('development')
  }
});
```

```
{
  "jsx": "react",
  "jsxFactory": "h",
}
```

```
```

