# react-js
React little projects

--------------------------------------------------------------------------------------------------------------------------------------
React needs to be installed and imported
----------------------------------------

class Button extends React.Component{
	state = { counter: 0};
  handleClick = () => {
  	this.props.onClickFunction(this.props.incrementValue);
  };
  
	render(){
		return (
			<button onClick={this.handleClick}>
      	+{this.props.incrementValue}
      </button>
		);
	}
}


const Result = (props) => {
	return (
		<div>{props.counter}</div>
	);
};


class App extends React.Component{
	state = { counter: 0};
	
  incrementCounter = (incrementValue) => {
  	this.setState((prevState) => ({
  		counter: prevState.counter + incrementValue
 		}))
  };
	render(){
  	return(
    <div>
    	<Button onClickFunction={this.incrementCounter} incrementValue={1} />
      <Button onClickFunction={this.incrementCounter} incrementValue={5} />
      <Button onClickFunction={this.incrementCounter} incrementValue={10} />
      <Button onClickFunction={this.incrementCounter} incrementValue={100} />
      <Result counter={this.state.counter} />
    </div>
    )
  }
}

ReactDOM.render(<App />, mountNode);
--------------------------------------------------------------------------------------------------------------------------------------
Listng and adding cards to a cardlist using Github API
---------------------

const Card = (props) => {
	return(
  <div>
  	<img width="75" src={props.avatar_url} />
    <div style={{display: 'inline-block', marginLeft: 10}}>
    	<div style={{fontSize: '1.25em', fontWeight: 'bold'}}>
      	{props.name}
      </div>
      <div>{props.company}</div>
    </div>
  </div>
  );
};

const CardList = (props) => {
	return(
  <div>
    	{props.cards.map(card => <Card {...card} />)}
  </div>
  
  );
}

class Form extends React.Component{
	handleSubmit = (event) => {
  //....
  }
  
	render(){
  		return(
    		<form onSubmit={this.handleSubmit}>
      		<input type="text" placeholder="Github Username" required />
          <button type="submit">Add card</button>
      	</form>
    	);
  }
}

class App extends React.Component{
	state = {
  	cards: [
    	{name:"Papa", avatar_url:"https://avatars2.githubusercontent.com/u/8445?v=3", company:"facebook"},
			{name:"Papa", avatar_url:"https://avatars2.githubusercontent.com/u/8445?v=3", company:"facebook"}
    ]
  };
  
  render(){
  	return(
    	<div>
      	<Form />
        <CardList cards={this.state.cards} />
      </div>
    )
  }
}

ReactDOM.render(<App />, mountNode);
