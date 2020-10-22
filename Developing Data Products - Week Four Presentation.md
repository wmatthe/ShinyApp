Developing Data Products - Week Four Presentation
========================================================
author: William Matthews
date: October 22, 2020
autosize: true

Assignment
========================================================

The assignment is to create a shiny app which includes the following: 

1. User input.
2. Operation on the ui.R file int he server.R file. 
3. Output that displays the server calculations. 
4. Documenation

My shiny app can be found here: https://wmatt.shinyapps.io/Iris_K_Means/

The code for the shiny app can be found here: https://github.com/wmatthe/ShinyApp


Overview
========================================================

This app allows the user to vizualize the Iris dataset using the k-means algorithm. 
The user select the x and y variables as the Sepal Length, Sepal Width, Petal Lenght, or Petal Width using a drop down box. 
The user also selects the Cluster count. The output is automatically updated on the plot. 

ui.R Code
========================================================

## library(shiny)

## vars <- setdiff(names(iris), "Species")

## pageWithSidebar(
## headerPanel('Iris k-means clustering'),
##  sidebarPanel("Change the variables to see how the plot changes.",
##    selectInput('xcol', 'X Variable', vars),
##    selectInput('ycol', 'Y Variable', vars, selected = vars[[2]]),
##    numericInput('clusters', 'Cluster count', 3, min = 1, max = 9)
##  ),
##  mainPanel(
##    plotOutput('plot1')
##  )
## )

server.R Code
========================================================

## function(input, output, session) {
  
##  # Combine the selected variables into a new data frame
##  selectedData <- reactive({
##    iris[, c(input$xcol, input$ycol)]
##  })
  
##  clusters <- reactive({
##    kmeans(selectedData(), input$clusters)
##  })
  
##  output$plot1 <- renderPlot({
##    palette(c("#E41A1C", "#377EB8", "#4DAF4A", "#984EA3",
##              "#FF7F00", "#FFFF33", "#A65628", "#F781BF", "#999999"))
    
##    par(mar = c(5.1, 4.1, 0, 1))
##    plot(selectedData(),
##         col = clusters()$cluster,
##         pch = 20, cex = 3)
##    points(clusters()$centers, pch = 4, cex = 4, lwd = 4)
##  })
  
## }


