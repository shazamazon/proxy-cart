# Shazamazon Proxy and Cart Functionality

### About

<a href="https://github.com/shazamazon/module-cart">Shazamazon Cart</a> is a full stack, responsive, e-commerce product reviews service delivered as a microservice, inspired by Amazon.

It was built as part of a <a href="https://github.com/shazamazon">e-commerce product page MVP</a> but can be used as a stand-alone cart and pricing section or combined with other services/components to create a full e-commerce site.

In addition to the cart and pricing section, I also developed this proxy to bring all the distributed microservices together, whose developers you can see below.

### Contributors

Cart service and proxy developed by <a href="https://github.com/jkcryptolock">jkcryptolock</a>, other components to the full e-commerce site devloped by:

<a href="https://github.com/SeanMcCarthy3223">SeanMcCarthy3223</a> - NavBar and Search

<a href='https://github.com/JeffSalinas'>JeffSalinas</a> - Carousel

<a href='https://github.com/Jibbscript'>Jibbscript</a> - Q&A

<a href='https://github.com/jxkim'>jxkim</a> - Product Images

<a href='https://github.com/ArohanD'>ArohanD</a> - Product Ratings

<a href='https://github.com/wiggitywhitney'>wiggitywhitney</a> - Product Description

### Tech Stack

_Hackmazon Cart Service_ was built primarily with ReactJS on the front end, Node/Express on the backend, and MongoDB for the database.

<img src="https://lh3.googleusercontent.com/ZIHOUCCxFaB7NirPhEX4K8cyTPIMvxvdJxpuhjb_qJ_dk-z7qEgD8riaR0ODXzXQZYn23zHpFiwGzxTDT88FTLeUMoPqlIjyLKoL1am8MH5pCoJExjL8SUC8uaeeiAjvQB0_vym6" width="100"/>
<img src="https://lh5.googleusercontent.com/_RcI-sgNRX5J0olXzRycjQN3tysoTXbH8kXRfE0AtBY8KkDrINApsrfZGAkczZYGwKTPZlYdJXQyKmWO4zFzvON9Op6Ovcu0GQxwabxWfGJH__oRB6YCC-qD_3b2yj_efkprD8UP" width="100" />
<img src="https://lh5.googleusercontent.com/rdAoVdYKOCnmtev6t7DJrEY7mG4iYsRPqeTH0Z-OrlsVmiea3q5SMtOGNSa7HzJcyxcIcelTacG5gPNgyBoIviiNcLbohQAicvpldcfM32Klb_ewouDRd67OtYhUAU1CEZB4rBqB" width="100" />
<img src="https://lh6.googleusercontent.com/tKlT8lGB2bTDqSilr_a2y8vaO-QBUdcUIYASnslf-RAKTxUEiEBq-_gTVBP0irIP1ZWNuSvp1fouOJrQBXUr0joVmBZzNyOec4jBpOyVogPZMOYhPH6YQwYOiLdZnfuaDnFel9rn" width="100" />
<img src="https://cloud.mongodb.com/static/images/mdb_logo.svg" width='100'/>

### Technical Challenges / Research

Some unexpected issues I ran into while building this app:

1. Reconciling different CSS configurations for each component, to get them to all display correctly via the proxy server.

2. Deciding whether to use a broadcast channel, or custom event dispatch and listeners to get microservices to communicate.

#### User Stories

- As a User, I should be able to see the price of the current item.
- As a User, I should be able to see Shazamazon prime qualification based on price.
- As a User, I should be able to add the item to my cart, and have it communicated to the NavBar.
- As a User, I should be able be able to click buy-it-now and confirm my purchase in a modal.

### Minimum Viable Product (MVP)

The MVP of the app displays all the relevant price and shipping info, based on the current product.

### How the App Works

Behind the scenes, the app takes in products, prices, and sellers, stores them in Mongo, and creates a query based upon the current product id.

When imported as a script to a page and given a div with an ID of 'cart-app', _Hackmazon Cart_ renders a complete cart section to the page via React.

It also communicates to the nav-bar by sending the current quantity of items selected when 'add-to-cart' is clicked, which updates the number of items displayed in the cart.

The proxy imports the javascript and css files for each microservice from their respective EC2 servers, and inserts them into a single HTML page based upon their React div ids. Custom Events are created and dispatched to individual event listeners in each component to update the product for each component.
